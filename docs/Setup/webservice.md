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
  *(This means that all libraries in `requirements.txt` will be installed)*
4. If there is a variable `Start Command`, set it to `gunicorn app:app & python3 -u bot.py & wait`, else you'll have to set up a [Procfile](#Content%20files)
  *(This runs the python files `app.py` and `bot.py`)*
5. You'll have to set up 2 environment variables. Set `user` to your Chat username, and `pass` to your Chat password
  *(Store your login info to keep it safe, as your code might be visible to others)*

*Need help with any of these steps? Contact me!*

### Content files
If you did everything correct, you should have a webserver that runs python now.
These files should be in your `main` branch:
#### `requirements.txt`
Containins all python libraries required by your bot. Gunicorn and Flask are required by app.py. Format:
```txt
gunicorn
Flask==3.0.3

customlibrary1
customlibrary2
```
#### `app.py`
This code will keep your service active 24/7. **Exact** content:
```py
from flask import Flask, jsonify
import os

app = Flask(__name__)

@app.route('/')
def ping():
    return jsonify({"success": "true"}), 200

if __name__ == "__main__":
    port = int(os.environ.get('PORT', 5000))
    app.run(host='0.0.0.0', port=port)
```
#### `bot.py`
This is the customisable code of your bot! Content is not specified yet.
#### `Procfile`
This file contains your build command, add it even with build command already set, and use this content:
```Procfile
web: gunicorn app:app & python3 -u bot.py & wait
```
