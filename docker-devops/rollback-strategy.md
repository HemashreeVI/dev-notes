# Rolling back safely

A deploy is only safe if you can undo it quickly.

**Checklist before shipping**
- The previous image/artifact is still available and tagged (`app:1.4.2`, never only `latest`).
- Database migrations are **backwards compatible**: old code still works on the new schema.
- Feature flags can turn new behaviour off without a deploy.

**Expand / contract migrations** (renaming a column):
1. Add the new column; write to both.
2. Backfill old rows.
3. Switch reads to the new column.
4. Later release: drop the old column.

At every step the previous version still runs, so rollback is just redeploying the old image.

```bash
kubectl rollout undo deployment/api           # Kubernetes
docker compose up -d api   # with the previous tag pinned in compose
```
