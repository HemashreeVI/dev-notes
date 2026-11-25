# Idempotency keys

A request is idempotent if sending it twice has the same effect as once. Networks retry, users double-click, so payment and booking endpoints need this.

GET, PUT and DELETE are idempotent by definition. POST isn't, so clients send a key:

```http
POST /payments
Idempotency-Key: 6f1c2e4a-...
```

Server side:

```text
1. Look up the key.
2. Found  -> return the stored response, do nothing else.
3. Missing -> do the work, store (key, response) atomically, return it.
```

**Details that matter**
- Store keys with a TTL (e.g. 24 h) and scope them per user.
- Use a unique constraint on the key so two concurrent first requests can't both run.
- If the same key arrives with a different body, return 422.
