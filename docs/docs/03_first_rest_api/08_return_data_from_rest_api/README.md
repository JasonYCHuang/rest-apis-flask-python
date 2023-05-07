---
title: 找到某個 store 與他的 items
description: How to use Flask to return data from your REST API to your client.
---

# 如何找到某個 store 與他的 items

使用 URL 參數，我們可以選擇特定 store

```py
@app.get("/store/<string:store_name>")
def get_store(store_name):
    for store in stores:
        if store["name"] == store_name:
            return store
    return {"message": "Store not found"}, 404
```

使用 `GET` 方法可以得到特定 store 的所有 items

```py
@app.get("/store/<string:store_name>/item")
def get_item_in_store(store_name):
    for store in stores:
        if store["name"] == store_name:
            return {"items": store["items"]}
    return {"message": "Store not found"}, 404
```
