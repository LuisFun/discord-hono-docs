---
title: TypeScript
sidebar:
  order: 3
---

```ts "Env" "CommandContext" "ComponentContext" "ModalContext" "CronContext"
import type {
  CommandContext,
  ComponentContext,
  ModalContext,
  CronContext,
} from 'discord-hono'
import { DiscordHono } from 'discord-hono'

type Env = {
  Bindings: {
    DB: D1Database
  }
}

const commandHandler = async (c: CommandContext<Env>) => {
  const db = c.env.DB
  /* 何かしらの処理 */
  return c.res({
    components: new Components().row(new Button('button', 'Yo!!')),
  })
}

const componentHandler = async (c: ComponentContext<Env>) => {
  const db = c.env.DB
  /* 何かしらの処理 */
  return c.resModal(
    new Modal('modal', 'これはモーダル').row(
      new TextInput('id', '何か入力して'),
    ),
  )
}

const modalHandler = async (c: ModalContext<Env>) => {
  const db = c.env.DB
  /* 何かしらの処理 */
  return c.res('モーダルが送信された')
}

const cronHandler = async (c: CronContext<Env>) => {
  const db = c.env.DB
  /* 何かしらの処理 */
}

const app = new DiscordHono<Env>()
  .command('hey', commandHandler)
  .component('button', componentHandler)
  .modal('modal', modalHandler)
  .cron('', cronHandler)
export default app
```

## import type

```ts
import type {
  CommandContext,
  ComponentContext,
  ModalContext,
  CronContext,
} from 'discord-hono'
```

それぞれの `app.***()` の第2引数で受け取ったコンテキストに対応します。
