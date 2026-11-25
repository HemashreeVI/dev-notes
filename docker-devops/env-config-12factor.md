# Config the 12-factor way

Keep config (anything that differs between dev, staging and prod) **out of code** and in environment variables.

| In code | In environment |
|---|---|
| business logic | database URLs |
| defaults | API keys, secrets |
| | feature flags, log level |

```yaml
# docker-compose.yml
services:
  api:
    env_file: .env          # dev values, never committed
```

```java
// Spring Boot reads env vars automatically:
// SPRING_DATASOURCE_URL -> spring.datasource.url
```

**Test:** could you open-source the repo right now without leaking a credential? If not, something belongs in the environment.
