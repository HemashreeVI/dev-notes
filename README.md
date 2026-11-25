# 📓 dev-notes

Short, practical notes on things I use as a backend / DevOps / AI engineer.
Each note is one page: the idea, a working example, and the gotchas.

84 notes, each added through its own pull request.

| Folder | What's inside |
|---|---|
| [`git/`](git) | everyday Git, fixing mistakes, internals |
| [`linux/`](linux) | shell, text processing, processes, permissions |
| [`docker-devops/`](docker-devops) | containers, compose, CI/CD, monitoring |
| [`backend/`](backend) | HTTP, APIs, databases, caching, reliability |
| [`dsa/`](dsa) | problem-solving patterns with templates |
| [`python-java/`](python-java) | language gotchas and idioms |
| [`system-design/`](system-design) | building blocks for scalable systems |

## 📚 Index

### Git (14)

- [Finding the bad commit with git bisect](git/bisect.md)
- [Working with remote branches](git/branches-remote.md)
- [git cherry-pick](git/cherry-pick.md)
- [How commit dates work](git/commit-dates.md)
- [Writing good commit messages](git/commit-messages.md)
- [Useful diff and log commands](git/diff-and-log.md)
- [Git internals in 5 minutes](git/git-internals.md)
- [.gitignore patterns](git/gitignore.md)
- [Cleaning up commits with interactive rebase](git/interactive-rebase.md)
- [Rebase vs merge](git/rebase-vs-merge.md)
- [Recovering "lost" work with reflog](git/reflog.md)
- [git stash](git/stash.md)
- [Tags and releases](git/tags-releases.md)
- [Undoing commits](git/undo-commits.md)

### Linux & shell (12)

- [awk for columns](linux/awk.md)
- [Safer bash scripts](linux/bash-scripting.md)
- [cron schedules](linux/cron.md)
- [Disk usage](linux/disk-usage.md)
- [Environment variables](linux/env-vars.md)
- [find and xargs](linux/find-xargs.md)
- [grep essentials](linux/grep.md)
- [File permissions](linux/permissions.md)
- [Pipes and redirection](linux/pipes-redirection.md)
- [Processes](linux/processes.md)
- [sed for quick edits](linux/sed.md)
- [SSH keys and config](linux/ssh.md)

### Docker & DevOps (12)

- [Blue-green vs canary deployments](docker-devops/blue-green-canary.md)
- [CI matrix builds](docker-devops/ci-matrix.md)
- [Docker Compose basics](docker-devops/compose-basics.md)
- [Dockerfile layer caching](docker-devops/dockerfile-layers.md)
- [Config the 12-factor way](docker-devops/env-config-12factor.md)
- [GitHub Actions basics](docker-devops/github-actions-basics.md)
- [Health checks](docker-devops/healthchecks.md)
- [Logging that helps at 3 a.m.](docker-devops/logging-best-practices.md)
- [Multi-stage builds](docker-devops/multi-stage-builds.md)
- [Prometheus metric types](docker-devops/prometheus-metrics.md)
- [Rolling back safely](docker-devops/rollback-strategy.md)
- [Volumes vs bind mounts](docker-devops/volumes-vs-bind-mounts.md)

### Backend (12)

- [Caching strategies](backend/caching-strategies.md)
- [CORS explained](backend/cors.md)
- [Database indexes](backend/database-indexes.md)
- [HTTP status codes worth knowing](backend/http-status-codes.md)
- [Idempotency keys](backend/idempotency.md)
- [JWT authentication](backend/jwt-auth.md)
- [The N+1 query problem](backend/n-plus-one.md)
- [Optimistic vs pessimistic locking](backend/optimistic-vs-pessimistic-locking.md)
- [Rate limiting algorithms](backend/rate-limiting.md)
- [REST API design checklist](backend/rest-api-design.md)
- [Retries with exponential backoff and jitter](backend/retries-backoff.md)
- [Transactions and isolation levels](backend/transactions-isolation.md)

### DSA patterns (14)

- [BFS: shortest path in unweighted graphs](dsa/bfs.md)
- [Binary search (the version that doesn't loop forever)](dsa/binary-search.md)
- [Complexity cheat sheet](dsa/complexity-cheatsheet.md)
- [DFS and backtracking](dsa/dfs-backtracking.md)
- [0/1 knapsack and its family](dsa/dp-knapsack.md)
- [DP on two strings](dsa/dp-on-strings.md)
- [Dynamic programming: how to start](dsa/dynamic-programming-intro.md)
- [Hashmap patterns](dsa/hashmap-patterns.md)
- [Heaps and top-k](dsa/heap-top-k.md)
- [Prefix sums](dsa/prefix-sums.md)
- [Sliding window](dsa/sliding-window.md)
- [Topological sort](dsa/topological-sort.md)
- [Two pointers](dsa/two-pointers.md)
- [Union-Find (Disjoint Set Union)](dsa/union-find.md)

### Python & Java (12)

- [Exceptions: good habits (Python and Java)](python-java/exceptions-best-practices.md)
- [Java concurrency basics](python-java/java-concurrency-basics.md)
- [Java: equals and hashCode](python-java/java-equals-hashcode.md)
- [Java Optional](python-java/java-optional.md)
- [Java streams](python-java/java-streams.md)
- [Python asyncio basics](python-java/python-asyncio.md)
- [Python comprehensions and generators](python-java/python-comprehensions.md)
- [Python context managers](python-java/python-context-managers.md)
- [Python dataclasses](python-java/python-dataclasses.md)
- [Python: mutable default arguments](python-java/python-mutable-defaults.md)
- [Python virtual environments](python-java/python-virtualenvs.md)
- [Spring Boot profiles and config](python-java/spring-boot-profiles.md)

### System design (8)

- [CAP theorem, practically](system-design/cap-theorem.md)
- [CDNs](system-design/cdn.md)
- [Consistent hashing](system-design/consistent-hashing.md)
- [Sharding and replication](system-design/database-sharding.md)
- [Load balancing](system-design/load-balancing.md)
- [Message queues and Kafka](system-design/message-queues-kafka.md)
- [Design: ticket booking without double-booking](system-design/ticket-booking-design.md)
- [Design: URL shortener](system-design/url-shortener-design.md)
