# Safer bash scripts

Start every script with:

```bash
#!/usr/bin/env bash
set -euo pipefail
```

| Flag | Effect |
|---|---|
| `-e` | exit on the first failing command |
| `-u` | error on undefined variables |
| `-o pipefail` | a pipeline fails if any part fails |

```bash
name="${1:?usage: deploy.sh <env>}"   # required argument with message
port="${PORT:-8080}"                  # default value
for f in *.log; do gzip "$f"; done    # always quote "$vars"
if [[ -f config.yaml ]]; then echo ok; fi
trap 'echo "failed at line $LINENO"' ERR
```

Run `shellcheck script.sh` to catch quoting bugs and other mistakes.
