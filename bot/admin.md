---
description: >-
  Learn how to configure hosting, manage staff access, and maintain the Mountain
  View RP bot.
icon: user-hat-tie
layout:
  width: wide
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: false
  pagination:
    visible: false
  metadata:
    visible: false
  tags:
    visible: true
  actions:
    visible: false
---

# Admin Guide

This guide explains how to run and administer the Mountain View RP bot.

The web dashboard is the intended way for both players and staff to interact with the bot. Admins should make sure the dashboard is reachable, Discord OAuth is configured, and staff roles are correct. Slash commands remain available as a fallback and for quick Discord-side actions.

### Admin Responsibilities

Admins are responsible for:

* bot hosting and uptime
* Discord OAuth setup for the dashboard
* staff/admin role configuration
* channel IDs and review channel setup
* slash command deployment
* plugin configs
* database backups
* resolving startup or hosting issues

### Important Files

* `config.json`: bot token, Discord application IDs, owner/guild IDs, dev mode.
* `configs/mv-rp-core/config.json`: staff/admin role IDs, audit channel, news channel, profile fields.
* `configs/mv-rp-dashboard/config.json`: dashboard host, port, public URL, OAuth secret, session secret.
* `configs/mv-rp-*/config.json`: plugin-specific settings.
* `data/mv-rp/database.sqlite`: main SQLite database.
* `data/mv-rp/*.sql`: owner-editable schema files.

Do not expose bot tokens, OAuth client secrets, session secrets, webhook tokens, or database backups publicly.

### Dashboard Setup

The dashboard should be the primary interface.

Required dashboard settings:

* `public_base_url`: the public URL users open in their browser.
* `discord_client_secret`: OAuth client secret from the Discord Developer Portal.
* `session_secret`: a long random secret.
* `guild_id`: leave blank to use `config.json.bot_ids.guild`, or set explicitly.

Recommended hosting environment variables:

```txt
MV_RP_DASHBOARD_PUBLIC_BASE_URL=https://your-dashboard-domain
MV_RP_DASHBOARD_DISCORD_CLIENT_SECRET=your_discord_oauth_secret
MV_RP_DASHBOARD_SESSION_SECRET=use_a_long_random_secret
```

The dashboard listens on the hosting platform's port when one is provided. It checks common variables such as `PORT`, `SERVER_PORT`, `APP_PORT`, `P_SERVER_PORT`, and `MV_RP_DASHBOARD_PORT`.

The dashboard should bind to `0.0.0.0` on hosted platforms.

Health check:

```txt
/health
```

If `/health` returns `ok`, the web server is reachable.

### Discord OAuth Setup

In the Discord Developer Portal, add the dashboard callback URL:

```txt
https://your-dashboard-domain/auth/discord/callback
```

For local testing:

```txt
http://127.0.0.1:3077/auth/discord/callback
```

The dashboard uses Discord OAuth with the `identify` scope, then checks guild membership through the bot.

### Staff And Admin Roles

Global staff permissions come only from RP Core config.

Set these in `configs/mv-rp-core/config.json`:

* `staff_role_ids`
* `admin_role_ids`

Staff and admin IDs are both treated as staff-level access by the bot.

After changing role IDs, restart the bot so the config reloads cleanly.

### Initial Staff Area

Use the dashboard if available. Discord fallback:

```txt
/rp-admin setup-staff-area
```

This creates staff-only channels and updates relevant config IDs for:

* audit logs
* property review
* business/shop review

After setup, check the generated config files and restart if needed.

### Slash Command Deployment

Deploy slash commands after adding, removing, or changing command definitions:

```txt
node deploy.js
```

Current RP commands include:

* `/character`
* `/rp-admin`
* `/rp-channel`
* `/money`
* `/property`
* `/time`
* `/weather`
* `/news`
* `/benefits`
* `/shop`
* `/job`

The dashboard has no slash command of its own.

### Starting The Bot

Start the bot with:

```txt
node bit.js
```

On startup, confirm that:

* all plugins load
* slash commands are already deployed
* the dashboard logs its listening address
* time status updates begin
* scheduled systems start

The dashboard startup log should look like:

```txt
Dashboard listening on 0.0.0.0:PORT
```

### Scheduled Systems

The bot runs several automatic systems:

* character proxying happens live in RP-enabled channels
* RP time updates continuously
* bot status shows current RP time
* weather updates use RP time intervals
* news quarter-hour reports run on startup and on schedule
* weekly news editions publish when due
* rent events are created and charged after grace
* social security summaries run on startup and once per RP week

If a scheduled system looks stuck, check startup logs, dashboard audit logs, and the relevant config.

### Database And Backups

The main database is:

```txt
data/mv-rp/database.sqlite
```

Back it up before:

* schema changes
* manual database edits
* major plugin changes
* moving hosts

Do not edit the SQLite database directly unless you know exactly what needs changing.

### Admin Troubleshooting

Dashboard does not load:

* confirm `/health` works
* confirm the host binds to `0.0.0.0`
* confirm the hosting port environment variable is being used
* confirm `public_base_url` matches the real public domain

Discord OAuth fails:

* confirm `discord_client_secret` is set
* confirm the callback URL exactly matches the Developer Portal redirect
* confirm the user is in the configured guild

Staff controls missing:

* confirm the user has a configured staff/admin role
* confirm role IDs are in `configs/mv-rp-core/config.json`
* restart the bot after config changes

Proxying fails:

* confirm the channel/category is enabled with `/rp-channel settings`
* confirm the bot can manage webhooks
* check proxy audit logs

Commands missing:

* run `node deploy.js`
* confirm the bot application ID is correct
* wait for Discord command propagation

### Admin Safety Rules

* Keep secrets out of chat and public repos.
* Use the dashboard for most staff/admin work.
* Prefer config files over direct database edits.
* Back up the database before risky changes.
* Use clear reasons for economy changes.
* Announce major time skips before running them.
* Treat proxy audit logs as private staff records.
