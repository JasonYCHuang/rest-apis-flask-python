---
title: 開始設置
description: Set up a Flask project and create the Flask app.
---

# 開始設置

建立 conda 環境，並且啟用

```
conda create --name tutorial-flask-01 python=3.9
conda activate tutorial-flask-01
```

安裝 Flask.

```
pip install flask
```

建立一個檔案 `app.py` ，用於 Flask app

```py title="app.py"
from flask import Flask

app = Flask(__name__)
```

現在你可以執行 Flask 命令列 Command-Line Interface (CLI):

```
flask run
```

但目前 Flask 還沒有辦法做任何事情.
