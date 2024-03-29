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
  /* Perform some operation */
  return c.res({
    components: new Components().row(new Button('button', 'Yo!!')),
  })
}

const componentHandler = async (c: ComponentContext<Env>) => {
  const db = c.env.DB
  /* Perform some operation */
  return c.resModal(
    new Modal('modal', 'This is Modal').row(
      new TextInput('id', 'Type something'),
    ),
  )
}

const modalHandler = async (c: ModalContext<Env>) => {
  const db = c.env.DB
  /* Perform some operation */
  return c.res('Modal Submit')
}

const cronHandler = async (c: CronContext<Env>) => {
  const db = c.env.DB
  /* Perform some operation */
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

It corresponds to the context received as the second argument of each `app.***()`.
