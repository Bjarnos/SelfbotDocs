---
title: BotService
parent: Services
nav_order: 1
---

# BotService

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

The BotService is a [service](/docs/Services/index.md) used to create new bots.

## BotService.create_bot()
<p style="font-size: 0.9rem; color: #6c757d;">V1.0.0+</p>

```py
BotService.create_bot(username : str, password : str, params : dict) -> [Bot](https://google.com)
```
This function allows you to create new bots, returns a new [Bot](/docs/Class/Bot) object.
```py
# Example code
from ChatSelfbot import BotService
bot = BotService.create_bot()
if bot.login("USERNAME HERE", "PASSWORD HERE"):
    print("log in succesful")
else:
    print("log in failed")
```
