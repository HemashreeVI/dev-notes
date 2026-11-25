# Transactions and isolation levels

ACID: **A**tomic (all or nothing), **C**onsistent, **I**solated, **D**urable.

| Level | Prevents | Still possible |
|---|---|---|
| Read Uncommitted | nothing | dirty reads |
| Read Committed (Postgres default) | dirty reads | non-repeatable reads, lost updates |
| Repeatable Read (MySQL default) | + non-repeatable reads | write skew |
| Serializable | everything | (transactions may be aborted; retry them) |

**Lost update example:** two requests read `stock = 1`, both write `stock = 0`, two orders succeed.

Fixes:

```sql
UPDATE products SET stock = stock - 1 WHERE id = 5 AND stock > 0;  -- atomic, check rows affected
SELECT stock FROM products WHERE id = 5 FOR UPDATE;               -- lock the row
```
