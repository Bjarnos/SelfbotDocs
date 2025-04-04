---
title: Selfhost
parent: Setup
nav_order: 2
---

# Selfhost

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

*We expect that you are using Visual Studio Code to selfhost, with all python extensions installed*

## Step 1. Install required libraries

### Create a virtual environment
1. Open an empty folder
2. Add a file named `bot.py` (or anything like that, as long as it's python), and set the source to:
```py
from ChatSelfbot import BotService
print("Hello world!")
```
4. Press `ctrl + shift + P`, and then select `Python: Create Environment...`
5. Select `Venv`, the download will start and might take a short while
6. Press `ctrl + shift + P` again and now select `Python: Create Terminal`
7. Run the command `.venv\Scripts\Activate` in the terminal, a green (.venv) tag will appear
8. Go ahead and run `pip install ChatSelfbot`, this will install the newest verion of our library
9. Now run `py bot.py` in the terminal (replace bot if you used a different name)
10. Did it print hello world without errors? Great! Now continue step 2
    *(if there are errors, contact me!)*

---

## Step 2. Your first code!
Go to `bot.py`, and set the code to this (make sure to replace "username" with your username and "password" with your password!):
```py
from ChatSelfbot import BotService
if BotService.login("username", "password"):
    messages = BotService.MessageService
    messages.create_post("Hello! I am a selfbot :D")
```
Run the command `py bot.py` again in your terminal and go to [Chat](https://chat.jonazwetsloot.nl/timeline?sort=time), did a new message by you appear? In that case you succesfully connected selfbot, read through the rest of the documentation to create the best selfbot of them all!

Remember: your ChatSelfbot won't automatically update! Keep track of announcements in Chat and download the newest update by running `pip install --upgrade ChatSelfbot` in your terminal!
