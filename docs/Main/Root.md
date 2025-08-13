---
title: Root
parent: Main
nav_order: 2
---

These are all methods directly derived from the library's root.

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

{: .note }
It is recommended to check out the [Bot](/docs/Main/Bot.md) and [Bot](/docs/Main/Bot.md) classes, as they are referenced in this article

---

# Methods
## ChatSelfbot.create_session()
<p style="font-size: 0.9rem; color: #6c757d;">V1.0.0+</p>

```py
ChatSelfbot.create_session(username : str, password: str) -> Bot | None
```
This function will create a new [Bot](/docs/Main/Bot.md) session, and return it.
Returns `None` if there was an error creating the bot.
```py
# Example code, confirms the username of the bot
import ChatSelfbot as selfbot
bot = selfbot.create_session("USERNAME", "PASSWORD")
if bot: # 'bot' might be None at error
    @bot.event
    async def on_ready():
        print((await bot.user()).username)

    bot.run()
```

