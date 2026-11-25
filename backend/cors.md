# CORS explained

Browsers block JavaScript on `app.example.com` from reading responses from `api.other.com` unless the API allows it. CORS is that permission. It's enforced by the **browser**, not the server; curl ignores it.

For "non-simple" requests (JSON body, custom headers, PUT/DELETE) the browser first sends a **preflight**:

```http
OPTIONS /orders
Origin: https://app.example.com
Access-Control-Request-Method: POST
```

The API must answer:

```http
Access-Control-Allow-Origin: https://app.example.com
Access-Control-Allow-Methods: GET, POST
Access-Control-Allow-Headers: Content-Type, Authorization
Access-Control-Allow-Credentials: true      # only if sending cookies
```

**Gotcha:** `Allow-Origin: *` can't be combined with credentials. List exact origins instead.
