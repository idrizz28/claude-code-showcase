# OAuth token refresher

I built a small Cloudflare Worker for a GHL Marketplace app.

## Concept

- An agency installs the app once, at agency level.
- The Worker stores the agency connection in Cloudflare's key-value storage.
- When a script needs to work in one sub-account, the Worker hands out short-lived
  access for that sub-account only. Requests to the Worker are protected by a key.
- A daily scheduled job refreshes every stored connection before it expires, so
  nothing breaks overnight.
- Secrets are set in Cloudflare's secret store and never committed.
