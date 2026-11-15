# Social Videos resolver

Deploy this folder on a Linux Docker host behind a public HTTPS reverse proxy. Copy `.env.example` to `.env`, copy `keys.example.json` to `keys.json`, generate one UUIDv4 and use the same UUID as the JSON key and Neon Function `MEDIA_RESOLVER_TOKEN`. Start with `docker compose up -d`.

Keep port 9000 private behind the proxy/firewall. Configure Neon Function `MEDIA_RESOLVER_URL` to the public HTTPS Cobalt endpoint and `MEDIA_RESOLVER_TOKEN` to that UUID. The backend uses the Cobalt `Api-Key` authorization header.

Cobalt handles video/MP3 conversion and quality selection. Social Videos extracts thumbnails from public Open Graph metadata where available. WhatsApp and Telegram are detected but not yet extractable by this resolver integration. Do not bypass DRM, private posts, login walls or access controls. Review Cobalt's AGPL-3.0 license before operating a public service.