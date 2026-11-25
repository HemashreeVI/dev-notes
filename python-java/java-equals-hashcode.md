# Java: equals and hashCode

If you override `equals`, you **must** override `hashCode`. Otherwise `HashMap` and `HashSet` break.

```java
class Seat {
    String row; int number;

    @Override public boolean equals(Object o) {
        if (this == o) return true;
        if (!(o instanceof Seat s)) return false;
        return number == s.number && row.equals(s.row);
    }
    @Override public int hashCode() { return Objects.hash(row, number); }
}
```

**Contract:** equal objects → equal hash codes (not necessarily the other way round).

**Easier:** a `record` generates both:

```java
record Seat(String row, int number) {}
```

**Gotcha:** don't use mutable fields in `hashCode`. Change one after inserting into a `HashSet` and the object becomes unfindable.
