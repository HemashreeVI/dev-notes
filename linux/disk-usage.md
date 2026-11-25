# Disk usage

```bash
df -h                              # free space per filesystem
du -sh *                           # size of each item here
du -sh * | sort -h | tail          # biggest last
du -h --max-depth=1 /var | sort -h
ncdu /                             # interactive explorer (install it)
docker system df                   # space used by Docker
docker system prune -a             # remove unused images/containers (careful)
journalctl --vacuum-size=200M      # shrink systemd logs
```

**Classic surprise:** `df` says full but `du` can't find it. A deleted file is still held open by a process. Find it with `lsof +L1` and restart that process.
