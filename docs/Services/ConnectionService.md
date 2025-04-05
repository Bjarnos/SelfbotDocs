---
title: ConnectionService
parent: Services
nav_order: 2
---

# ConnectionService

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

The ConnectionService is a [service](/docs/Services/index.md) used to run specific functions when a message is received.
The service is split in 2 parts, Public Service (for handling public posts) and DM Service (for handling DMs/group chats).

## Public Service
### ConnectionService.bind_to_public_post()
<p style="font-size: 0.9rem; color: #6c757d;">V1.0.0+</p>

```py
ConnectionService.bind_to_public_post(func : function) -> None
```
This function will run argument `func` every time that a new public post is created, and pass a [PublicMessage](/docs/Classes/PublicMessage) as the first argument.
```py
# Example code, likes every new message received
from ChatSelfbot import BotService, Classes
if BotService.login("USERNAME HERE", "PASSWORD HERE"):
    connections = BotService.ConnectionService
    def f1(message: Classes.PublicMessage):
        message.like()
    connections.bind_to_public_post(f1)
    connections.start_checking_public() # required!
```

### ConnectionService.bind_to_message_reply()
<p style="font-size: 0.9rem; color: #6c757d;">V1.0.0+</p>

```py
ConnectionService.bind_to_message_reply(message_id : str, func : function) -> None
```
This function will run argument `func` every time that there's replied to the message with id message_id, and pass a [PublicMessage](/docs/Classes/PublicMessage) (the reply) as the first argument.
```py
# Example code, likes every new reply
from ChatSelfbot import BotService
if BotService.login("USERNAME HERE", "PASSWORD HERE"):
    connections = BotService.ConnectionService
    def f1(message: Classes.PublicMessage):
        message.like()
    def f2(message: Classes.PublicMessage):
        connections.bind_to_message_reply(message.id, f1)
    connections.bind_to_public_post(f2)
    connections.start_checking_public() # required!
```
*Note that this example code can be done more effective with [PublicMessage.bind_to_reply()](#empty)*
