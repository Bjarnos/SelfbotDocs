---
title: BotService
parent: Setup
nav_order: 1
---

# BotService

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

The BotService is a [service](/docs/Services/index.md) used to control other services and your bot.

Variables and functions:

## BotService.ConnectionService
-# V1.0.0+
A direct link to the [ConnectionService](/docs/Services/ConnectionService.md). For example code, check out the ConnectionService's documentation.

## BotService.MessageService
-# V1.0.0+
A direct link to the [MessageService](/docs/Services/MessageService.md). For example code, check out the MessageService's documentation.

## BotService.ProfileService
-# V1.0.0+
A direct link to the [ProfileService](/docs/Services/ProfileService.md). For example code, check out the ProfileService's documentation.

## BotService.login()
-# V1.0.0+
```py
BotService.login(username : str, password : str, params : dict) -> bool
```
This function allows you to log in to your account, so that you can begin with using your selfbot. Returns True or False, True is login succesful and False is login failed.
```py
# Example code
from ChatSelfbot import BotService
if BotService.login("USERNAME HERE", "PASSWORD HERE"):
    print("log in succesful")
else:
    print("log in failed")
```
Possible params, as of V1.0.0 (values set are the standard values):
```json
{
  'http-log' = False,
  'check-own' = True,
  'force-first' = False
}
```

### http-log
When set to `True`, prints every http request and it's result code in the output.

### check-own
When set to `False`, the bot will ignore all of it's own messages when checking public messages/reply.

### force-first
When you use
