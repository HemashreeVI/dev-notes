# Spring Boot profiles and config

```text
src/main/resources/
  application.yml          # shared defaults
  application-dev.yml      # overrides for dev
  application-prod.yml     # overrides for prod
```

Activate one:

```bash
SPRING_PROFILES_ACTIVE=prod java -jar app.jar
```

**Bind config to a typed class:**

```java
@ConfigurationProperties(prefix = "booking")
public record BookingProps(int holdSeconds, int maxSeatsPerOrder) {}
```

```yaml
booking:
  hold-seconds: 300
  max-seats-per-order: 6
```

**Precedence (highest first):** command-line args → environment variables (`BOOKING_HOLDSECONDS`) → profile yml → `application.yml`. Secrets come from the environment, never from committed yml.
