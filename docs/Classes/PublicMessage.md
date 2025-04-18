---
title: PublicMessage
parent: Classes
nav_order: 2
---

# BotService

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

The PublicMessage class is a [class](/docs/Classes/index.md) that contains data and useful functions for a sent message.

## Variables
### time
<p style="font-size: 0.9rem; color: #6c757d;">V1.1.0+</p>
The epoch time that the publicmessage was sent, as float. 0 or None if an error occures.
```py
# Example code, prints the time of every new public post
from ChatSelfbot import BotService, Classes
PublicMessage = Classes.PublicMessage
bot = BotService.create_bot()
if bot.login("USERNAME HERE", "PASSWORD HERE"):
    connections = bot.ConnectionService
    def f1(message: PublicMessage):
        print(message.time)
    connections.bind_to_public_post(f1)
    connections.start_checking_public() # required!
```

### text
<p style="font-size: 0.9rem; color: #6c757d;">V1.1.0+</p>
The content text of a message, without markdown.
```py
# Example code, prints the content of every new public post
from ChatSelfbot import BotService, Classes
PublicMessage = Classes.PublicMessage
bot = BotService.create_bot()
if bot.login("USERNAME HERE", "PASSWORD HERE"):
    connections = bot.ConnectionService
    def f1(message: PublicMessage):
        print(message.text)
    connections.bind_to_public_post(f1)
    connections.start_checking_public() # required!
```

### markdowntext
<p style="font-size: 0.9rem; color: #6c757d;">V1.1.0+</p>
The original text of a message, including markdown.
```py
# Example code, prints the original text of every new public post
from ChatSelfbot import BotService, Classes
PublicMessage = Classes.PublicMessage
bot = BotService.create_bot()
if bot.login("USERNAME HERE", "PASSWORD HERE"):
    connections = bot.ConnectionService
    def f1(message: PublicMessage):
        print(message.markdowntext)
    connections.bind_to_public_post(f1)
    connections.start_checking_public() # required!
```

### sender
<p style="font-size: 0.9rem; color: #6c757d;">V1.1.0+</p>
The name of the sender of the message.
```py
# Example code, prints the sender name of every new public post
from ChatSelfbot import BotService, Classes
PublicMessage = Classes.PublicMessage
bot = BotService.create_bot()
if bot.login("USERNAME HERE", "PASSWORD HERE"):
    connections = bot.ConnectionService
    def f1(message: PublicMessage):
        print(message.sender)
    connections.bind_to_public_post(f1)
    connections.start_checking_public() # required!
```

### id
<p style="font-size: 0.9rem; color: #6c757d;">V1.1.0+</p>
The id of a message commonly used for replies.
```py
# Example code, prints the id of every new public post
from ChatSelfbot import BotService, Classes
PublicMessage = Classes.PublicMessage
bot = BotService.create_bot()
if bot.login("USERNAME HERE", "PASSWORD HERE"):
    connections = bot.ConnectionService
    def f1(message: PublicMessage):
        print(message.id)
    connections.bind_to_public_post(f1)
    connections.start_checking_public() # required!
```

## like()
<p style="font-size: 0.9rem; color: #6c757d;">V1.1.0+</p>

A link to [MessageService.like()](https://docs.bjarnos.dev/docs/Services/MessageService.html#messageservicelike), but the message_id is automatically filled.
```py
# Example code, creates and likes a new post
from ChatSelfbot import BotService
bot = BotService.create_bot()
if bot.login("USERNAME HERE", "PASSWORD HERE"):
    messages = bot.MessageService
    success, m = messages.create_post("Hello everyone! I'm a selfbot.")
    print(success)
    if success:
        messages.like(id)
```

