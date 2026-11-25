# Python dataclasses

Less boilerplate for classes that mostly hold data.

```python
from dataclasses import dataclass, field

@dataclass(frozen=True, slots=True)
class Seat:
    row: str
    number: int
    tags: list[str] = field(default_factory=list)

s = Seat("C", 14)
print(s)                      # Seat(row='C', number=14, tags=[])
s == Seat("C", 14)            # True: __eq__ generated
```

| Option | Effect |
|---|---|
| `frozen=True` | immutable, hashable (usable as dict keys) |
| `slots=True` | less memory, faster attribute access |
| `order=True` | adds `<`, `>` comparisons |

For validation of external input (API bodies), use Pydantic models instead.
