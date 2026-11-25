# Docker Compose basics

```yaml
services:
  api:
    build: .
    ports: ["8080:8080"]          # host:container
    environment:
      DB_URL: postgres://app:app@db:5432/app   # "db" = service name = hostname
    depends_on:
      db: { condition: service_healthy }
  db:
    image: postgres:16
    environment: { POSTGRES_USER: app, POSTGRES_PASSWORD: app, POSTGRES_DB: app }
    volumes: [pgdata:/var/lib/postgresql/data]
    healthcheck:
      test: ["CMD-SHELL", "pg_isready -U app"]
      interval: 5s
volumes:
  pgdata:
```

```bash
docker compose up -d --build
docker compose logs -f api
docker compose down          # add -v to also delete volumes (data!)
```

**Gotcha:** inside the network, services talk on the *container* port (`db:5432`), not the host-mapped one.
