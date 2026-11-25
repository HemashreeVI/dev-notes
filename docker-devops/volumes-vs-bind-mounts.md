# Volumes vs bind mounts

| | Named volume | Bind mount |
|---|---|---|
| Syntax | `pgdata:/var/lib/postgresql/data` | `./src:/app/src` |
| Managed by | Docker | you (a host folder) |
| Use for | database data, persistent state | live code reload in development |
| Portable | yes | depends on host paths |

```bash
docker volume ls
docker volume inspect pgdata
docker run --rm -v pgdata:/data -v "$PWD":/backup alpine \
  tar czf /backup/pgdata.tgz -C /data .     # back up a volume
```

**Gotcha:** a container's own filesystem disappears when the container is removed. Anything that must survive goes in a volume.
