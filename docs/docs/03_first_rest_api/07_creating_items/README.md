---
title: 如何在每個 stroe 中創建 items
description: A brief description of the lecture goes here.
---

# 如何創建 items

以下為執行步驟 :

1. client 端會發送 store name，這個 name 指定了 item 要被加入哪一個 store.
2. 也會提供 item 的 name 與 price.
3. 遍歷 store ，已找到吻合 name 的 store.
4. 把新建的 item 加到這個 store 的 `items` 內.

## URL 參數

client 端有幾個放式可以傳送資料：

- JSON body (在 POST 與 PUT 請求)
- 在 URL 內 (在 GET 與 DELETE 請求)
- 在請求標頭 (request headers).

:::info

幾個 URL 的例子

- `/store/My Store/item`
- `/store/another-store/item`
- `/store/a/item`

在著三個 URL 內"store name" 為：

- `My Store`
- `another-store`
- `a`

:::

因此，把部分資訊放在 URL 內會更清楚，如 `POST /store/My Store/item`, 而不是 `POST /add-item` 並把 store name 置入 JSON body.

```py
@app.route("/store/<string:name>/item")
```

函式 function 會使用 `name` 參數

```py title="app.py"
from flask import Flask, request

app = Flask(__name__)

stores = [{"name": "My Store", "items": [{"name": "my item", "price": 15.99}]}]


@app.get("/store")
def get_stores():
    return {"stores": stores}


@app.post("/store")
def create_store():
    request_data = request.get_json()
    new_store = {"name": request_data["name"], "items": []}
    stores.append(new_store)
    return new_store, 201


# highlight-start
@app.post("/store/<string:store_name>/item")
def create_item(store_name): # store_name 由 URL 參數提供
    request_data = request.get_json()
    for store in stores:
        if store["name"] == store_name:
            new_item = {"name": request_data["name"], "price": request_data["price"]} # 此處的 name 為 item_name
            store["items"].append(new_item)
            return new_item
    return {"message": "Store not found"}, 404
# highlight-end
```

:::tip 以上代碼並非最佳化

在這個接口，我們遍歷所有 stores 直到找到相對應的 `store_name`，這並非有效率，在之後使用 database 章節，我們會使用有效率的方式.

:::
