# MultiBotDash

MultiBotDash is a web dashboard for managing one or more Discord bots and their per-server settings from a single, user-friendly interface.

The application provides OAuth-based login with Discord, server configuration pages, command lists, auto-responder management, and internal notification support for bot instances.

## Features

- Discord OAuth 2.0 login and server management.
- Per-server settings and permissions management.
- Auto-responder creation and management for automated replies.
- Commands listing and server-level command configuration.
- Bot notification endpoints for internal integrations.
- Simple UI pages for dashboards, server overview, and command docs (see `public/`).

## Quick start

1. Copy `.env.example` to `.env` and fill in the values described below.

2. Install dependencies:

```bash
npm install
```

3. Start the server:

```bash
npm start
```

4. In development, run with auto-reload (requires `nodemon`):

```bash
npm run dev
```

By default the server runs on port `3001`. To change it, set the `PORT` environment variable.

## Environment variables

Populate `.env` (or your hosting provider's environment configuration) with the following variables. Use `.env.example` as a reference.

- `PORT` — port to run the server on (default 3001)
- `BASE_URL` — base URL used for OAuth redirects (for example `http://localhost:3001`)
- `MONGODB_URI` — MongoDB connection string used by the app
- `DISCORD_CLIENT_ID` — Discord OAuth application client id
- `DISCORD_CLIENT_SECRET` — Discord OAuth application client secret
- `BOT_TOKEN` — (optional) Discord bot token for server-managed bot actions
- `BOT_NOTIFY_TOKEN` — (optional) shared secret used for internal notification endpoints

Do not commit real secrets to version control. Keep `.env` in `.gitignore` and use environment injection on hosting platforms.

## Project layout (important files)

- `src/` — server source code
	- `server.js` — Express server entry
	- `database/` — DB connection helpers
	- `models/` — Mongoose models (users, configuration)
- `public/` — static client pages (dashboard UI, server pages, command docs)
- `api/` — API routes and server-side endpoints
- `auth/` — OAuth and authentication helpers (Discord)

Open `public/` to preview client pages such as `dashboard.html`, `server.html`, and `commands.html`.

## Typical usage

1. Visit the site and log in via Discord.
2. Authorize the application for the servers you manage.
3. Use the dashboard to configure per-server settings, add or edit auto-responders, and view available commands.

## Development notes & contribution

- Follow existing code style and keep secrets out of commits.
- If you add new environment variables, document them here and add defaults to `.env.example` when appropriate.
- Small pull requests and issues are welcome.

## Security

- Rotate any credentials that were exposed prior to switching to environment variables.
- Validate and sanitize any input that could be stored or displayed to prevent injection or XSS.

## License

MIT

---

If you want me to tailor this README more specifically to a hosted deployment (Heroku, Vercel, Fly, Docker) or to add a short troubleshooting section, tell me which target and I'll update the file accordingly.
