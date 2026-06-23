---
description: >-
  Learn how to review applications, manage staff tools, and handle moderation
  workflows in the Mountain View RP bot.
icon: clipboard-user
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

# Staff Guide

This guide explains how to use the Mountain View RP bot as staff.

The web dashboard is the intended staff interface. Use the dashboard for review queues, audits, economy moderation, weather, time, news, property, shops, jobs, and benefits. Slash commands are still available for quick actions from Discord, but the dashboard should be the normal place to work.

### Staff Role

Staff access comes from the staff/admin roles configured by the server admins. If you cannot see staff controls in the dashboard or staff-only commands fail, check that your Discord account has the correct staff role.

### Staff Dashboard Workflow

Use the dashboard first for:

* reviewing property and shop applications
* checking character and proxy audit history
* managing listings, weather, time, news, and benefits
* inspecting balances and ledgers
* running grants, takes, and balance corrections
* managing jobs and business oversight

Every dashboard write action is audited with your Discord user ID.

### Character Oversight

Staff can inspect characters and help players with character issues.

Useful commands:

* `/rp-admin characters` lists characters in the server.
* `/rp-admin character` inspects one character.
* `/character list user:@User` lists another user's characters.
* `/character view` views a character profile.

Staff can also remove bad triggers or help players correct character fields.

### RP Channel Controls

RP proxying only works in enabled channels or categories.

Use the dashboard staff audit/control page when possible.

Discord fallback:

* `/rp-channel enable` enables proxying in a channel or category.
* `/rp-channel disable` disables proxying.
* `/rp-channel settings` checks the current setting.

When enabling a category, all channels inside that category can inherit the setting.

### Proxy And Audit Review

Use staff audit tools to investigate proxy issues.

Check:

* whether the channel is RP-enabled
* whether the player has an active character in that channel
* whether a trigger matched the message
* whether the bot could create or use a webhook
* whether the original message was deleted after proxying

Proxy audit logs include message content and attachment metadata, so treat them as staff-only moderation records.

### Economy Moderation

Use the dashboard for balance corrections and ledger review.

Discord fallback:

* `/money grant` gives money to a character.
* `/money take` removes money from a character.
* `/money set` sets a character balance.
* `/money ledger` reviews recent transactions.

Use clear reasons for all staff economy changes. The economy ledger is meant to explain why money moved.

### Property Review

Property applications are character-based.

Use the dashboard review queue when possible.

Discord fallback:

* `/property listing create` creates a sale or rental listing.
* `/property applications list` lists applications.
* `/property applications view` views an application.
* `/property applications approve` approves an application.
* `/property applications deny` denies an application.

When approving a property, decide whether to:

* charge the character now
* create a private property channel
* attach an existing channel
* leave a review note

Rent events are created automatically. If rent is unpaid past grace, it can become debt.

### Property Channel Access

Property owners can grant or revoke access for Discord users.

Staff can help with:

* `/property access grant`
* `/property access revoke`
* `/property access list`

Access is granted to Discord users, not individual characters, because channel permissions are Discord-user based.

### Shops And Business Review

Shops require approved property.

Use the dashboard review queue when possible.

Discord fallback:

* `/shop applications list`
* `/shop applications approve`
* `/shop applications deny`
* `/shop view`
* `/shop service list`
* `/shop manager list`

Shop owners and managers can manage services. Staff can step in when needed.

### Jobs

Jobs are paid tasks posted by characters.

Staff can oversee the job board and resolve disputes.

Useful commands:

* `/job list`
* `/job view`
* `/job accept`
* `/job complete`
* `/job cancel`

Completing a job pays the accepted worker automatically from the posting character.

### Benefits

Social security benefits are temporary weekly basic income.

Use the dashboard Benefits page to review summaries and run the weekly cycle if needed.

Discord fallback:

* `/benefits summary`
* `/benefits preview`
* `/benefits run`

The public summary should show totals and tier counts only. It should not list character names.

### Time

Staff can manage the RP clock.

Use the dashboard Time page when possible.

Discord fallback:

* `/time current`
* `/time zones`
* `/time set`
* `/time advance`
* `/time pause`
* `/time resume`
* `/time area set`
* `/time area remove`
* `/time skip run`
* `/time skip schedule`
* `/time skip list`
* `/time skip cancel`

Use time skips carefully because weather, rent, and benefits can depend on RP time.

### Weather

Weather is simulated per location.

Use the dashboard Weather page when possible.

Discord fallback:

* `/weather current`
* `/weather forecast`
* `/weather locations`
* `/weather set`
* `/weather reroll`

The global news/weather reports summarize current weather for players.

### News

Use the dashboard News page to manage stories and publishing.

Discord fallback:

* `/news story add`
* `/news story list`
* `/news story view`
* `/news story edit`
* `/news story archive`
* `/news report now`
* `/news edition preview`
* `/news edition publish`

Quarter-hour reports are routine updates. Weekly editions publish queued stories.

### Good Staff Habits

* Prefer the dashboard for any action that needs review or context.
* Use slash commands for quick in-channel work.
* Leave clear notes when approving or denying applications.
* Give economy changes specific reasons.
* Avoid changing RP time without warning players.
* Check audit logs before assuming a player made a mistake.
* Keep staff-only information out of public channels.
