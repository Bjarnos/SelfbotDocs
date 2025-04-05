---
title: MessageService
parent: Services
nav_order: 3
---

# ConnectionService

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

The MessageService is a [service](/docs/Services/index.md) used to send and modify messages.

## MessageService.create_post()
<p style="font-size: 0.9rem; color: #6c757d;">V1.0.0+</p>

```py
MessageService.create_post(message : str) -> bool
```
This function create a new public post, returns `(True, message_id)` if the request succeeded and `(False, None)` if the request failed.
The rate limit (set by Chat, not by selfbot) is 1 post/reply every 1.5 seconds.
```py
# Example code, creates a new post
from ChatSelfbot import BotService
if BotService.login("USERNAME HERE", "PASSWORD HERE"):
    messages = BotService.MessageService
    messages.create_post("Hello everyone! I'm a selfbot.")
```

## MessageService.reply()
<p style="font-size: 0.9rem; color: #6c757d;">V1.0.0+</p>

```py
MessageService.reply(message_id : str, message : str) -> Tuple[bool, str]
```
This function create a new reply to a public post, returns `(True, message_id)` if the request succeeded and `(False, "0")` if the request failed.
The rate limit (set by Chat, not by selfbot) is 1 post/reply every 1.5 seconds.
```py
# Example code, creates and replies to a new post
from ChatSelfbot import BotService
import time
if BotService.login("USERNAME HERE", "PASSWORD HERE"):
    messages = BotService.MessageService
    success, id = messages.create_post("Hello everyone! I'm a selfbot.")
    print(success)
    if success:
        time.sleep(2)
        success, id = messages.reply(id, "Replied!")
        print(success)
```


## MessageService.like()
<p style="font-size: 0.9rem; color: #6c757d;">V1.0.0+</p>

```py
MessageService.like(message_id : str, value : bool = True) -> bool
```
This function create a new reply to a public post, returns `True` if the request succeeded and `False` if the request failed.
```py
# Example code, creates and likes a new post
from ChatSelfbot import BotService
if BotService.login("USERNAME HERE", "PASSWORD HERE"):
    messages = BotService.MessageService
    success, id = messages.create_post("Hello everyone! I'm a selfbot.")
    print(success)
    if success:
        messages.like(id)
```

## MessageService.edit()
<p style="font-size: 0.9rem; color: #6c757d;">V1.0.0+</p>

```py
MessageService.edit(message_id : str, message : str) -> bool
```
This function edits a public post, returns `True` if the request succeeded and `False` if the request failed.
```py
# Example code, creates a new post and edits it
from ChatSelfbot import BotService
if BotService.login("USERNAME HERE", "PASSWORD HERE"):
    messages = BotService.MessageService
    success, id = messages.create_post("Hello everyone! I'm a selfbot.")
    print(success)
    if success:
        messages.edit(id, "[deleted]") # this does not actually delete it
```

## MessageService.delete()
<p style="font-size: 0.9rem; color: #6c757d;">V1.0.0+</p>

```py
MessageService.delete(message_id : str) -> bool
```
This function deletes a public post, returns `True` if the request succeeded and `False` if the request failed.
```py
# Example code, creates a new post and deletes it after 20 seconds
from ChatSelfbot import BotService
import time
if BotService.login("USERNAME HERE", "PASSWORD HERE"):
    messages = BotService.MessageService
    success, id = messages.create_post("Hello everyone! I'm a selfbot.")
    print(success)
    if success:
        time.sleep(20)
        messages.delete(id)
```

## MessageService.direct_message()
<p style="font-size: 0.9rem; color: #6c757d;">V1.0.0+</p>

```py
MessageService.direct_message(username : str, message : str) -> bool
```
This function sends a direct message to a user (you don't have to follow them), returns `True` if the request succeeded and `False` if the request failed.
```py
# Example code, send a dm to the creator of every new post
from ChatSelfbot import BotService, Classes
if BotService.login("USERNAME HERE", "PASSWORD HERE"):
    connections = BotService.ConnectionService
    messages = BotService.MessageService
    def f1(message: Classes.PublicMessage):
        messages.direct_message(message.sender, "What a funny post you just sent!")
    connections.bind_to_public_post(f1)
    connections.start_checking_public()
```

## MessageService.get_group_id_by_name()
<p style="font-size: 0.9rem; color: #6c757d;">V1.0.0+</p>

```py
MessageService.get_group_id_by_name(group_name : str) -> str
```
This function returns the id of a group.

## MessageService.message_group_by_name()
<p style="font-size: 0.9rem; color: #6c757d;">V1.0.0+</p>

```py
MessageService.message_group_by_name(group_name : str, message : str) -> bool
```
This function sends a message to a group chat, returns `True` if the request succeeded and `False` if the request failed.
```py
# Example code, replies to new posts in a group chat
from ChatSelfbot import BotService, Classes
if BotService.login("USERNAME HERE", "PASSWORD HERE"):
    connections = BotService.ConnectionService
    messages = BotService.MessageService
    def f1(message: Classes.DMMessage):
        if message.groupname:
            messages.message_group_by_name(message.groupname, "I received a message!")
    connections.bind_to_any_dm(f1)
    connections.start_checking_dms()
```


## MessageService.message_group_by_id()
<p style="font-size: 0.9rem; color: #6c757d;">V1.0.0+</p>

```py
MessageService.message_group_by_id(group_id : str, message : str) -> bool
```
This function sends a message to a group chat, returns `True` if the request succeeded and `False` if the request failed.
```py
# Example code, replies to new posts in a group chat
from ChatSelfbot import BotService, Classes
if BotService.login("USERNAME HERE", "PASSWORD HERE"):
    connections = BotService.ConnectionService
    messages = BotService.MessageService
    def f1(message: Classes.DMMessage):
        if message.groupname:
            messages.message_group_by_id(messages.get_group_id_by_name(message.groupname), "I received a message!")
    connections.bind_to_any_dm(f1)
    connections.start_checking_dms()
```
