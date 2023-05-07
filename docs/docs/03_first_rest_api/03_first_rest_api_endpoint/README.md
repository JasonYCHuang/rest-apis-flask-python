---
title: 第一個 REST API 接口
description: Learn how to define a REST API endpoint using Flask.
---

# 第一個 REST API 接口

對於大部分專案，數據會儲存在 database ．現在，為了簡化，數據儲存在 Python list.

在後面的課程，數據會儲存在 database．

```py title="app.py"
from flask import Flask

app = Flask(__name__)

stores = [{"name": "My Store", "items": [{"name": "my item", "price": 15.99}]}] # 數據儲存
```

建立第一個路由 (route)，它會回傳所有 stores 數據.

```py title="app.py"
from flask import Flask

app = Flask(__name__)

stores = [{"name": "My Store", "items": [{"name": "my item", "price": 15.99}]}]


@app.get("/store")
def get_stores():
    return {"stores": stores}
```

## Flask 路由 route 架構

Flask 路由 (route) 有兩部分:

- 裝飾子 decorator
- 要執行的函式 function

裝飾子 (`@app.get("/store")`) 將此 `/store` 接口 _註冊_ 到 Flask. 當 Flask 接收到 `/store`，它會執行此 函式 function `get_stores`.

要執行的函式 function 最後有一回傳值，在此我們回傳 JSON，但也可回傳 (e.g. XML, HTML, YAML, plain text, 等等).
