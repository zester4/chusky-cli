# Chusky CLI

The official terminal client for Chusky. It connects to a deployed Chusky
service and shares the authenticated user's durable session with Telegram and
the web dashboard. The agent and provider credentials remain on the server;
this package never runs a local Composio session.

## Install

```bash
npm install -g @chusky/cli
chusky auth link --server https://chusky.up.railway.app
chusky chat
```

In Telegram, send `/cli link` to generate a one-time pairing code. The CLI
stores the resulting device token in the operating system credential store
(with an encrypted-file fallback when a keychain is unavailable).

Use `chusky help` for commands. Meeting controls, calendars, participant
context, voice selection, connected apps, triggers, tasks, reminders, files,
workers, approvals, and durable runs are available through the same account
session as the other Chusky channels.

For a checkout that also contains the Chusky service, the retained local
configuration commands are available as `chusky setup` and `chusky doctor`.
The published client itself does not start a Telegram or HTTP service; it
connects to the configured Chusky server.

## Development

```bash
npm install
npm run typecheck
npm test
npm run build
node dist/cli.js chat
```

Set `CHUSKY_SERVER_URL` to override the saved server URL. Do not place a
project API key or server secret in this client; pairing uses a short-lived
Telegram code and the returned device token is treated like a password.
