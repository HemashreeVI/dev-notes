# Load balancing

Spreads requests across servers so none is overloaded and a dead one is skipped.

| Algorithm | Picks | Good for |
|---|---|---|
| Round robin | next server in turn | similar servers, similar requests |
| Least connections | server with fewest open connections | long or uneven requests |
| Weighted | by capacity | mixed machine sizes |
| Hash (IP / key) | same client → same server | sticky sessions, caches |

**Layer 4** (TCP) is fast and blind to content. **Layer 7** (HTTP) can route by path or header (`/api` → API servers, `/static` → CDN).

**Must-haves:** health checks to remove bad servers, and stateless app servers (sessions in Redis, not memory) so any server can take any request.
