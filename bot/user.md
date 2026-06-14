---
description: >-
  Learn how to create characters, proxy messages, manage money, and use player
  features in the Mountain View RP bot.
icon: user
layout:
  width: default
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
  metadata:
    visible: true
  tags:
    visible: true
  actions:
    visible: true
---

# User Guide

This guide explains how to use the Mountain View RP bot as a player.

Most features are built around your RP characters. Characters can talk through webhooks, hold their own money, apply for property, own shops, post jobs, and receive weekly benefits.

The web dashboard is the intended way to interact with the bot day to day. Slash commands still work inside Discord and are useful when you are already in a channel, but the dashboard is the main place to manage characters, money, applications, shops, jobs, and benefits.

### Quick Start

1. Open the web dashboard and sign in with Discord.
2. Create a character from the Characters page.
3. Go to an RP channel in Discord.
4. Set your active character from the dashboard or with `/character switch`.
5. Type normally in that channel.
6. The bot will repost your message as your active character and delete your original message.

Discord-only quick start:

1. Create a character with `/character create`.
2. Go to an RP channel.
3. Set your active character with `/character switch`.
4. Type normally in that channel.
5. The bot will repost your message as your active character and delete your original message.

Your active character is set per channel. Switching in one channel does not automatically switch you everywhere else.

### Characters

Characters are your RP identities. You can have as many as you need.

Use:

* `/character create` to make a new character.
* `/character edit` to update one field on a character.
* `/character delete` to delete one of your characters.
* `/character list` to see your characters.
* `/character view` to view a character profile.
* `/character switch` to set your active character for a channel.

When creating a character, useful fields include:

* `name`: the display name used for proxied messages.
* `avatar_url`: image URL used as the webhook avatar.
* `pronouns`: public pronouns.
* `bio`: short public bio.
* `tags`: quick descriptors.
* `notes`: private notes field.

### Speaking As A Character

There are two ways to proxy messages.

#### Active Character

Use `/character switch` in a channel, then type normally.

Example:

```txt
/character switch character:Alex
```

After that, messages you send in that RP channel will be reposted as Alex.

This only works in channels or categories where staff have enabled RP proxying.

#### Bracket Triggers

Triggers let you speak as a character without switching active character first.

Use:

* `/character trigger add`
* `/character trigger list`
* `/character trigger remove`

Example trigger:

```txt
Prefix: [[
Suffix: ]]
```

Then write:

```txt
[[Hey, is anyone at the cafe?]]
```

The bot will proxy the message as that trigger's character.

Triggers can override your active character for that message.

### Money

Each character has their own balance.

Use:

* `/money balance` to check a character's balance.
* `/money pay` to pay another character.
* `/money ledger` to view recent transactions.

If you do not choose a character, money commands usually try to use your active character for the current channel.

Example:

```txt
/money pay to_character:Sam amount:50 from_character:Alex reason:Lunch
```

Staff-only economy commands such as grant, take, and set are not normal player tools.

### Benefits

Social security benefits are temporary basic income for characters who do not have enough money yet.

Benefits are checked per character, not per Discord account.

Use:

* `/benefits status` to see a character's current benefit tier.
* `/benefits history` to see recent benefit payouts.
* `/benefits summary` to see the weekly server summary.

The weekly summary shows:

* total paid that RP week
* total number of recipients
* recipient count per paying tier
* characters evaluated but not paid
* characters skipped because they have an automatic job

The public summary does not list character names.

### Property And Rent

Characters can apply for listed properties or custom unlisted properties.

Use:

* `/property listing list` to see active listings.
* `/property listing view` to inspect one listing.
* `/property listing apply` to apply for a listed property.
* `/property apply-custom` to apply for an unlisted property.
* `/property access grant` to give another Discord user access to one of your private property channels.
* `/property access revoke` to remove that access.
* `/property access list` to see who has access.
* `/property rent status` to see pending rent.
* `/property rent pay` to pay a pending rent event.

Property ownership is character-based. Discord channel access is user-based, so when you grant access you grant it to a Discord user.

Rent can become debt if it is not paid before the grace period ends.

### Shops

Shops are character-owned businesses attached to approved properties.

Use:

* `/shop apply` to apply to open a shop at one of your approved properties.
* `/shop list` to list approved shops.
* `/shop view` to view a shop and its services.
* `/shop service add` to add a service to a shop you manage.
* `/shop service remove` to remove one of your shop services.
* `/shop service list` to list a shop's services.
* `/shop service buy` to buy a service as one of your characters.
* `/shop manager add` to add a Discord user as a shop manager.
* `/shop manager remove` to remove a shop manager.
* `/shop manager list` to list managers.

Buying a service transfers money from the buyer character to the shop owner character.

### Jobs

Jobs are paid RP tasks posted by characters.

Use:

* `/job post` to post a paid job.
* `/job list` to browse jobs.
* `/job view` to inspect one job.
* `/job apply` to apply for a job as a character.
* `/job accept` to accept an application for a job you posted.
* `/job complete` to mark an accepted job complete and pay the worker.
* `/job cancel` to cancel an open or accepted job you posted.

Job payment moves money from the posting character to the accepted worker character when the job is completed.

### Time

Mountain View uses an accelerated RP clock.

Use:

* `/time current` to see the current RP time.
* `/time zones` to see configured RP time areas.

Staff can change the clock, pause it, resume it, advance it, and schedule time skips.

### Weather

Weather is simulated per RP location.

Use:

* `/weather current` to view one location.
* `/weather forecast` to view all current weather.
* `/weather locations` to see configured locations.

Staff can manually set or reroll weather.

### News

The bot can post quarter-hour reports and weekly news editions.

As a player, you mainly read these in the configured news channel.

Staff can queue stories, post reports, and publish weekly editions.

### Dashboard

The web dashboard is the primary interface for the bot. Sign in with Discord and use it whenever you need to manage things outside a live RP conversation.

Players can use the dashboard to:

* manage their own characters
* view balances and ledgers
* apply for property
* manage property access
* apply for shops
* manage shop services and managers
* post and manage jobs
* view benefits, time, weather, and news

Staff will see additional control-room tools.

Slash commands are still available as a fallback and for quick actions while you are already in Discord.

### Common Tips

* If a command asks for a character, use Discord autocomplete when available.
* If a command says it needs an active character, run `/character switch` in that channel first.
* If your message does not proxy, make sure you are in an RP-enabled channel.
* If a bracket trigger does not work, check `/character trigger list`.
* If you cannot manage a shop, property, or job, make sure it belongs to one of your characters or that you are listed as a manager.
* If money commands fail, your paying character may not have enough balance.

### Example First Session

```txt
/character create name:Alex pronouns:they/them bio:New arrival in Mountain View
/character switch character:Alex
```

Then type in an RP channel:

```txt
Alex steps into the diner and looks for an empty booth.
```

The bot reposts that as Alex.

Then check your money:

```txt
/money balance character:Alex
```

Apply for a place:

```txt
/property listing list
/property listing apply listing_id:1 character:Alex message:I would like to rent this apartment.
```

Check benefits:

```txt
/benefits status character:Alex
```
