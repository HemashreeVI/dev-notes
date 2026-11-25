# The N+1 query problem

```python
orders = Order.objects.all()            # 1 query
for o in orders:
    print(o.customer.name)              # +1 query per order -> N+1
```

100 orders = 101 round trips. Fast locally, slow in production.

**Fix: load related data in one go.**

```python
Order.objects.select_related("customer")      # Django: JOIN
Order.objects.prefetch_related("items")       # Django: 2nd query with IN (...)
```

```java
@Query("select o from Order o join fetch o.customer")   // JPA / Hibernate
```

**Spot it:** turn on SQL logging and count queries per request, or use tools like django-debug-toolbar or Hibernate statistics.
