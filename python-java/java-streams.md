# Java streams

```java
List<String> names = users.stream()
    .filter(u -> u.isActive())
    .map(User::getName)
    .sorted()
    .toList();

Map<String, List<Order>> byStatus = orders.stream()
    .collect(Collectors.groupingBy(Order::getStatus));

double total = orders.stream().mapToDouble(Order::getAmount).sum();

Optional<User> admin = users.stream().filter(User::isAdmin).findFirst();
```

**Rules**
- Streams are lazy: nothing runs until a terminal operation (`toList`, `collect`, `sum`...).
- A stream can be consumed only once.
- Don't modify outside state inside `map`/`filter`.
- `parallelStream()` only pays off for large, CPU-heavy, independent work.
