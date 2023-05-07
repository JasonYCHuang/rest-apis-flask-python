---
title: 如何建立 stores
description: Learn how to add data to our REST API.
---

# 如何建立 stores

由 client 發送 JSON 請求 (request) (可用 Insomnia、curl 或另一個 python app)

請求包含 store 的 name，我們需要把他加入 database

這裡使用 `POST` 請求. `POST` 同常用於創建資料.

為了可以得到請求的 JSON 內容, 需要由 `flask` 引入 `request`.

```py
from flask import Flask, request
```

接著，建立接口

```py title="app.py"
# highlight-start
from flask import Flask, request
# highlight-end

app = Flask(__name__)

stores = [{"name": "My Store", "items": [{"name": "my item", "price": 15.99}]}]


@app.get("/store")
def get_stores():
    return {"stores": stores}


# highlight-start
@app.post("/store")
def create_store():
    request_data = request.get_json()
    new_store = {"name": request_data["name"], "items": []}
    stores.append(new_store)
    return new_store, 201
# highlight-end
```

使用 `request.get_json()` 得到請求 (request) 的 JSON 內容.

建立 `new_store` object/dictionary 代表 store. 它含有 `name` 與 `items` (空的 list).

接著把 `new_store` append 到原有的 `stores` list.

最後，返回新建的 `new_store`，以告訴 client 端我們已成功建立一筆新的 store.

:::tip 回傳狀態代碼 (status code)
每個回傳都有 status code ， 告訴 client 端我們的 request 是否成功的被 server 處理．其中 `404` 是 Not Found (接口未被找到)

最常用的 status code 是 `200`，表示 "OK".

若我們要回傳不同的 status code ，可以把它放在接口 function 的第二個值.

在 `create_store()` 中，我們回傳 `201`，表示 "已建立".
:::
