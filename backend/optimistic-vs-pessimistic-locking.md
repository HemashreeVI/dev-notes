# Optimistic vs pessimistic locking

**Pessimistic:** lock first, then work.

```sql
BEGIN;
SELECT * FROM seats WHERE id = 14 FOR UPDATE;   -- others wait here
UPDATE seats SET booked_by = 7 WHERE id = 14;
COMMIT;
```

**Optimistic:** work freely, check a version when writing.

```sql
UPDATE seats SET booked_by = 7, version = version + 1
WHERE id = 14 AND version = 3;     -- 0 rows updated => someone else won, retry or fail
```

| | Pessimistic | Optimistic |
|---|---|---|
| Best when | conflicts are frequent | conflicts are rare |
| Cost | waiting, possible deadlocks | retries |

JPA: `@Version` on a field gives optimistic locking; `@Lock(PESSIMISTIC_WRITE)` gives `FOR UPDATE`.

For very hot items (one seat, many buyers), a distributed lock or a queue in front may beat both.
