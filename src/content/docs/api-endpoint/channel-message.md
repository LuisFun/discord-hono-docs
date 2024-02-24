---
title: Channel Message
---

```ts
import { DiscordHono, postMessage } from 'discord-hono'

const app = new DiscordHono()
app.command('ping', async c => {
  const token = c.env.DISCORD_TOKEN
  const channelId = c.interaction.channel.id
  await postMessage(token, channelId, 'Another post')
  return c.res('Response post')
})

export default app
```

## postMessage()

```ts
await postMessage('DISCORD_TOKEN', 'Channel ID', 'string or data', ...files)
```

The third argument is a string or [APIInteractionResponseCallbackData](https://discord-api-types.dev/api/next/discord-api-types-v10#APIInteractionResponseCallbackData).

## deleteMessage()

```ts
await deleteMessage('DISCORD_TOKEN', 'Channel ID', 'Message ID')
```

## followupMessage()

```ts
await followupMessage(
  'Application ID',
  'Interaction Token',
  'string or data',
  ...files,
)
```

The third argument is a string or [APIInteractionResponseCallbackData](https://discord-api-types.dev/api/next/discord-api-types-v10#APIInteractionResponseCallbackData).

`c.followup()` uses this.

## followupDeleteMessage()

```ts
await followupDeleteMessage('Application ID', 'Interaction Token', 'Message ID')
```

`c.followupDelete()`, `c.resRepost()` uses this.