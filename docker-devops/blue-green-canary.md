# Blue-green vs canary deployments

**Blue-green:** run the new version (green) next to the old (blue), then switch all traffic at once.
- Instant rollback: switch back.
- Needs double capacity during the switch.

**Canary:** send a small share of traffic to the new version, watch metrics, then increase.

```text
v2: 1% -> 10% -> 50% -> 100%     (stop and roll back if errors or latency rise)
```

- Limits blast radius; real users test it gradually.
- Needs good metrics to decide automatically.

**Rolling update** (Kubernetes default) replaces pods a few at a time. Simple, but both versions serve at once, so the API and DB schema must stay compatible across versions.
