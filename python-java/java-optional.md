# Java Optional

`Optional` makes "might be missing" explicit in a return type.

```java
Optional<User> findByEmail(String email);

String name = repo.findByEmail(e)
    .map(User::getName)
    .orElse("guest");

User u = repo.findById(id)
    .orElseThrow(() -> new NotFoundException("user " + id));

repo.findById(id).ifPresent(this::sendWelcome);
```

**Do**
- Use it as a return type.

**Don't**
- Call `.get()` without checking. Use `orElseThrow()` so the intent is clear.
- Use `Optional` for fields or method parameters.
- Return `null` from a method declared to return `Optional`.
