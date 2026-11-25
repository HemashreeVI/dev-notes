# JWT authentication

A JWT is `header.payload.signature`, base64url-encoded. The payload is **readable by anyone**; the signature only proves it wasn't changed.

```json
{ "sub": "user_42", "role": "admin", "exp": 1764064800 }
```

**Typical flow**
1. Login → server returns a short-lived **access token** (5–15 min) and a long-lived **refresh token**.
2. Client sends `Authorization: Bearer <access>` on each request.
3. When it expires, the client trades the refresh token for a new access token.

**Rules**
- Always verify signature, `exp`, and the expected algorithm (reject `alg: none`).
- Never put secrets or personal data in the payload.
- Store refresh tokens server-side (or rotate them) so you can revoke sessions.
- In browsers prefer `HttpOnly`, `Secure`, `SameSite` cookies over `localStorage`.
