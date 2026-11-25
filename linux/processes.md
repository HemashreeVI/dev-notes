# Processes

```bash
ps aux | grep python         # list processes
pgrep -fa uvicorn            # PIDs + command lines matching a pattern
top / htop                   # live view
kill 1234                    # polite stop (SIGTERM, 15)
kill -9 1234                 # force kill (SIGKILL), no cleanup possible
pkill -f "celery worker"     # kill by pattern
lsof -i :8080                # what is using port 8080
ss -ltnp                     # listening TCP ports + processes
nohup ./server &             # keep running after logout
jobs; fg %1; bg %1           # shell job control
```

**Try SIGTERM first.** It lets the app close connections and flush data; SIGKILL can leave locks and half-written files behind.
