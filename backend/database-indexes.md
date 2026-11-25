# Database indexes

An index is a sorted structure (usually a B-tree) that turns a full scan into a lookup.

```sql
CREATE INDEX idx_orders_user_created ON orders (user_id, created_at DESC);

-- uses the index (leftmost prefix):
SELECT * FROM orders WHERE user_id = 7 ORDER BY created_at DESC LIMIT 20;
-- can't use it well (skips user_id):
SELECT * FROM orders WHERE created_at > now() - interval '1 day';
```

**Check, don't guess:**

```sql
EXPLAIN ANALYZE SELECT ...;   -- look for "Seq Scan" on big tables
```

**Costs:** every index slows writes and uses disk. Index columns you filter, join and sort on; skip low-cardinality columns like booleans.

**Gotcha:** wrapping the column in a function (`WHERE lower(email) = ...`) skips a normal index. Index the expression instead.
