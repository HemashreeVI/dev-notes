# cron schedules

```text
┌───── minute (0-59)
│ ┌─── hour (0-23)
│ │ ┌─ day of month (1-31)
│ │ │ ┌ month (1-12)
│ │ │ │ ┌ day of week (0-6, Sun=0)
* * * * *  command
```

| Schedule | Means |
|---|---|
| `*/5 * * * *` | every 5 minutes |
| `0 2 * * *` | 02:00 every day |
| `30 9 * * 1-5` | 09:30 on weekdays |
| `0 0 1 * *` | midnight on the 1st |

```bash
crontab -e        # edit your jobs
crontab -l        # list them
```

**Gotchas**
- cron runs with a tiny `PATH`; use absolute paths (`/usr/bin/python3`).
- Capture output or you'll never see errors: `... >> /var/log/job.log 2>&1`.
- GitHub Actions `schedule:` uses the same syntax, in UTC.
