# REST API design checklist

- **Nouns, plural:** `GET /orders`, `GET /orders/42`, `POST /orders`. No `/getOrder`.
- **Nest only one level:** `/orders/42/items`.
- **Methods mean things:** GET reads, POST creates, PUT replaces, PATCH updates partly, DELETE removes.
- **Filter, sort, paginate with query params:** `/orders?status=paid&sort=-created_at&limit=20`.
- **Consistent errors:**

```json
{ "error": { "code": "SEAT_TAKEN", "message": "Seat 14C is already booked", "request_id": "9f2c" } }
```

- **Version from day one:** `/v1/orders` or a header.
- **Return what you created** (201 + body + `Location`).
- **Timestamps in ISO 8601 UTC:** `2026-11-25T10:00:00Z`.
