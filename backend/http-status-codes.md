# HTTP status codes worth knowing

| Code | Use when |
|---|---|
| 200 OK | success with a body |
| 201 Created | resource created (return `Location` header) |
| 204 No Content | success, nothing to return (DELETE) |
| 400 Bad Request | malformed input |
| 401 Unauthorized | not authenticated (no/invalid token) |
| 403 Forbidden | authenticated but not allowed |
| 404 Not Found | resource doesn't exist |
| 409 Conflict | state conflict (seat already booked, version mismatch) |
| 422 Unprocessable Entity | well-formed but fails validation |
| 429 Too Many Requests | rate limited (send `Retry-After`) |
| 500 Internal Server Error | bug on our side |
| 502 / 503 / 504 | upstream bad / unavailable / timed out |

**Rule:** 4xx = the client should change something. 5xx = the server failed; retrying later might work.
