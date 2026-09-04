---
'manifest': patch
---

Add generic OIDC login to the dashboard. The backend generic-oauth plugin was already registered, but the client never surfaced it: register `genericOAuthClient` so `signIn.oauth2` is available, and render a button for the configured OIDC provider (via `OIDC_PROVIDER_ID`) on the login and register pages. Requires `OIDC_CLIENT_ID`, `OIDC_CLIENT_SECRET` and `OIDC_ISSUER`/`OIDC_DISCOVERY_URL`; the IdP callback is `${BETTER_AUTH_URL}/api/auth/oauth2/callback/${OIDC_PROVIDER_ID}`.
