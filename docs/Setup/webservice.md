---
title: Web Service
parent: Setup
nav_order: 1
---

# Web Service

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Step 1. Create a web service

### Recommended programs
- [Koyeb](https://koyeb.com)
- [Render](https://render.com)

### Webserver variables
When deploying the webserver:
1. Make sure `Language` is `Python 3`
2. The variable `Build Command` must be `pip install -r requirements.txt`
3. If there is a variable `Start Command`, set it to `gunicorn app:app & python3 -u bot.py & wait`, else you'll have to set up a [Procfile](#Content%20files)
4. You'll have to set up 2 environment variables. Set `user` to your Chat username, and `pass` to your Chat password

*Need help with any of these steps? Contact me!*

### Content files
If you did everything correct, you should have a webserver that runs python now.
These files should be in your `main` branch:
