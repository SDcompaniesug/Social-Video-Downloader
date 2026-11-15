# Social Videos

**Public website:** https://social-videos.vercel.app  
**GitHub source:** https://github.com/SDcompaniesug/Social-Video-Downloader

Social Videos is a free public downloader website with a separate developer portal.

## Website
- React + Vite source in `site/`
- Anonymous public downloader UI for video, MP3 and thumbnail formats
- Video quality and MP3 bitrate controls
- Browser media preview when the resolver returns a playable URL
- Neon Managed Auth developer registration/sign-in
- Developer dashboard for API key creation, listing, revocation, profile name and usage counters
- API documentation page

## Backend
- Neon Function: `socialvideos`
- Public MCP endpoint: `https://br-silent-sea-b97onfev-socialvideos.compute.c-7.eu-central-1.aws.neon.tech/mcp`
- Neon Postgres schema in `backend/schema.sql`
- API keys are returned once and stored as SHA-256 hashes
- Website downloads do not require an account; only API-key management does

## Media resolver
The backend integrates with a self-hosted, API-key-protected Cobalt service. See `resolver/`. Set Neon Function environment variables `MEDIA_RESOLVER_URL` and `MEDIA_RESOLVER_TOKEN` after deploying that service. Until then, requests fail explicitly instead of returning fake media links.

WhatsApp and Telegram links are recognized but are not yet supported by the current resolver adapter. Platform availability can change.

## Local website development
```bash
cd site
cp .env.example .env.local
npm install
npm run dev
```

## Security
Use only public content you own or are authorized to save. No private-post, DRM or login-wall bypass is implemented. Never commit production secrets.
