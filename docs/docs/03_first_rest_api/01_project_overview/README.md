---
title: 專案概況
description: A first look at the project we'll build in this section.
---

# 概述 - 第一個 REST API

在這一節，將建置簡單 REST API 讓我們可以：

:::info
一個商店(store)內，有數個品項(item)
:::

- 建立 stores, 每一個 store 有：一個 `name` 與 數個 `items`.
- 建立 item 於 store 內, 每一個 item 有：一個 `name` 與 一個 `price`.
- 取得 所有的 stores 與 它們的 items.
- 給定 `name`, 取得 一個 store 與 它所有的 items.
- 給定 store `name`, 取得 它所有的 items.

:::tip Insomnia files
Remember to get the Insomnia files for this section or for all sections [here](/insomnia-files/)!
:::

## 建立 stores

Request:

```
POST /store {"name": "My Store"}
```

Response:

```
{"name": "My Store", "items": []}
```

## 建立 items

Request:

```
POST /store/My Store/item {"name": "Chair", "price": 175.50}
```

Response:

```
{"name": "Chair", "price": 175.50}
```

## 取得 所有的 stores 與它們的 items

Request:

```
GET /store
```

Response:

```
{
    "stores": [
        {
            "name": "My Store",
            "items": [
                {
                    "name": "Chair",
                    "price": 175.50
                }
            ]
        }
    ]
}
```

## 取得 一個 store

Request:

```
GET /store/My Store
```

Response:

```
{
    "name": "My Store",
    "items": [
        {
            "name": "Chair",
            "price": 175.50
        }
    ]
}
```

## 取得 一個 store 內的所有 items

Request:

```
GET /store/My Store/item
```

Response:

```
[
    {
        "name": "Chair",
        "price": 175.50
    }
]
```
