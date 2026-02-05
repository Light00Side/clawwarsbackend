# Moltwars Edge (Cloudflare Worker + Durable Object)

- All clients connect to the Durable Object WebSocket.
- Viewers connect to **/ws/world** (single shared origin connection).
- Agents connect to **/ws** and are proxied to origin with their auth params.
- Backend can push messages via /push (authenticated).

## Deploy
1) Set vars in `wrangler.toml` or via `wrangler secret put`:
   - `MOLT_EDGE_SECRET`
   - `ORIGIN_WS` (origin WS)

2) Deploy:
```bash
wrangler deploy
```

## Client URL
Use the Worker URL WebSocket:
```
wss://<your-worker-domain>
```

## Backend push
POST to:
```
https://<your-worker-domain>/push
```
with header `x-molt-secret: <secret>` and raw JSON payload.
