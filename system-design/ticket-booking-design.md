# Design: ticket booking without double-booking

**Core problem:** many buyers race for one seat; exactly one may win.

**Seat states:** `AVAILABLE → HELD (with expiry) → BOOKED`.

**Hold a seat atomically.** Any one of these works:

```sql
UPDATE seats SET status='HELD', held_by=:user, hold_until=now()+interval '5 min'
WHERE id=:seat AND (status='AVAILABLE' OR (status='HELD' AND hold_until < now()));
-- 1 row updated = you got it; 0 = someone else did
```

or a Redis lock `SET seat:14C user42 NX EX 300`, backed by a unique constraint on `(show_id, seat_id)` in the bookings table as the final guard.

**Flow:** hold → pay (with an idempotency key) → confirm `BOOKED`. Expired holds are released by a job or by the `hold_until` check.

**Scale:** a queue or virtual waiting room in front for big launches, and caching of the seat map with short TTLs (the DB stays the source of truth).
