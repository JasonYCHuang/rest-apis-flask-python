---
title: '什麼是 JSON?'
description: JSON is the way we normally transfer data to and from REST APIs.
---

# 什麼是 JSON?

JSON 只是一個長字串，包含以下格式.

```json
{
  "key": "value",
  "another": 25,
  "listic_data": [1, 3, 7],
  "sub_objects": {
    "name": "Rolf",
    "age": 25
  }
}
```

他的值可以為：

- Strings
- Numbers
- Booleans (`true` or `false`)
- Lists
- Objects (akin to dictionaries 字典 in Python)
  - 鍵 (key) 無順序

在最上層，JSON 可為 object 或 list．以下為一個有效的 JSON:

```json
[
  {
    "name": "Rolf",
    "age": 25
  },
  {
    "name": "Anne",
    "age": 27
  },
  {
    "name": "Adam",
    "age": 23
  }
]
```

當回傳 Python dictionary 字典, Flask 會自動將它轉為 JSON，所以我們不需再轉一次.

有兩個轉換要特別注意:

1. 把 Python 關鍵字轉為 JSON 標準 (也就是轉 `True` 為 `true`).
2. 把整個 dictionary 轉為長字串.
