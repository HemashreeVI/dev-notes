# CDNs

A CDN caches content on servers near users, so a request from Chennai doesn't travel to a US data center.

**Good for:** images, JS/CSS, video, downloads, even cacheable API responses.

**Control it with headers:**

```http
Cache-Control: public, max-age=31536000, immutable   # fingerprinted assets: app.3f9a1.js
Cache-Control: no-store                               # private/personal data
Cache-Control: public, max-age=60, stale-while-revalidate=300
```

**Cache busting:** put a content hash in file names (`app.3f9a1.js`) so a new deploy gets new URLs and old ones can be cached forever.

Extras most CDNs add: TLS termination, DDoS protection, image resizing, edge functions.
