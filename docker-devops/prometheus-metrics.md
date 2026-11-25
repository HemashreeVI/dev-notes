# Prometheus metric types

| Type | Goes | Example |
|---|---|---|
| Counter | only up | `http_requests_total` |
| Gauge | up and down | `queue_depth`, `memory_bytes` |
| Histogram | buckets of observations | `http_request_duration_seconds` |

```python
from prometheus_client import Counter, Histogram
REQS = Counter("http_requests_total", "Requests", ["route", "status"])
LAT = Histogram("http_request_duration_seconds", "Latency", ["route"])
```

Useful PromQL:

```promql
rate(http_requests_total[5m])                                    # req/s
sum(rate(http_requests_total{status=~"5.."}[5m]))
  / sum(rate(http_requests_total[5m]))                            # error ratio
histogram_quantile(0.95, sum by (le) (rate(http_request_duration_seconds_bucket[5m])))  # p95
```

**Gotcha:** never put user IDs or other unbounded values in labels. Each label combination is a new time series.
