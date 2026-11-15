# Neon Function backend

Runtime: Node.js 24. Function slug: `socialvideos`. Public endpoints: `/health`, `/mcp`, `/api/health`, `/api/platforms`, `/api/resolve`, and developer endpoints `/api/keys`, `/api/usage`, `/api/me`. Developer API endpoint: `POST /v1/resolve`.

Neon Managed Auth verifies dashboard sessions using injected `NEON_AUTH_BASE_URL` and `NEON_AUTH_JWKS_URL`. Postgres connection is supplied by Neon as `DATABASE_URL`.

Set `MEDIA_RESOLVER_URL` and `MEDIA_RESOLVER_TOKEN` after deploying the protected Cobalt instance in `../resolver`. Until configured, media requests return a clear error rather than a fake media URL.

Apply `schema.sql` to the `social_videos` database. API keys are returned once and stored as SHA-256 hashes. The MCP endpoint is public and does not require an end-user account or a developer API key.