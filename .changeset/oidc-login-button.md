---
'manifest': patch
---

Add generic OIDC login to the dashboard. The backend registers the configured provider via the `genericOAuth` server plugin, and the dashboard renders a button for it (via `OIDC_PROVIDER_ID`) on the login and register pages using the standard `signIn.social` flow. Requires `OIDC_CLIENT_ID`, `OIDC_CLIENT_SECRET` and `OIDC_ISSUER`/`OIDC_DISCOVERY_URL`; the IdP callback is `${BETTER_AUTH_URL}/api/auth/oauth2/callback/${OIDC_PROVIDER_ID}`.
