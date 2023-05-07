---
title: How to interact with REST API
description: Use Postman and Insomnia REST Client to interact with your REST API.
---

# 向 REST API 發出請求

可以使用 Postman、Insomnia 發出請求

Insomnia 是免費 且是 open source.

先下載 [downloading Insomnia REST Client](https://insomnia.rest/).

建立一個專案 Project，取名為 "REST APIs with Flask and Python".

![Creating the Project for this course](assets/creating-project.png)

接著，建立一個請求集合，命名為 "Stores REST API".

![Creating the Stores REST API Request Collection](assets/making-request-collection.png)

In the Request Collection, we can now add requests! Each request has a few parts:

- A **method**, such as `GET` or `POST`. The method is just a piece of data sent to the server, but _usually_ certain methods are used for certain things.
- The **URL** that you want to request. For our API, this is formed of the "Base URL" (for Flask apps, that's `http://127.0.0.1:5000`), and the endpoint (e.g. `/store`).
- The **body**, or any data that you want to send in the request. For example, when creating stores or items we might send some data.
- The **headers**, which are other pieces of data with specific names, that the server can use. For example, a header might be sent to help the server understand _who_ is making the request.

Let's create our first request, `GET /store`.

Make a new request using the Insomnia interface. First, use the dropdown to start:

![How to make a request using the Insomnia interface](assets/making-request.png)

Then enter the request name. Leave the method as `GET`:

![Enter the request name and method](assets/set-request-name-and-method.png)

Once you're done, you will see your request in the collection:

![The request is shown in the collection](assets/before-setting-url.png)

Next up, enter the URL for your request. Here we will be requesting the `/store` endpoint. Remember to include your Base URL as well:

![Entering the full URL for the request in Insomnia](assets/url-set.png)

Once you're done, make sure that your Flask app is running! If it isn't, remember to activate your virtual environment first and then run the app:

```
source .venv/bin/activate
flask run
```

:::caution
The Flask app will run, by default, on port 5000. If you have another (or the same) app already running, you'll get an error because the port will be "busy".

If you get an error, read it carefully and make sure that no other Flask app is running on the same port.
:::

Once your Flask app is running, you can hit "Send" on the Insomnia client, and you should see the JSON come back from your API!

![Making a request to our API using Insomnia](assets/after-pressing-send.png)

If that worked and you can see your JSON, you're good to go! You've made your first API request. Now we can continue developing our REST API, remembering to always create new Requests in Insomnia and test our code as we go along!
