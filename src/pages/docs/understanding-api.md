---
title: Understanding API
description: Understanding the WhatsAPI API
---

This page contains information about the WhatsAPI API.

---

## Accessing the API

The swagger documentation is available on the `/api/docs/index.html` endpoint.

## Authenticating requests

As a security measure, all requests made to a `production` server must be authenticated with a `token`. This is the exact same token that you provided in the config file. You can also provide multiple tokens in the config file. In that case, you can use any of the tokens to authenticate your requests.

## What's an Instance?

The term `instance` refers to a WhatsApp Web session created on your server. This session is created using the WhatsAPI API. You can create multiple instances on your server.

Each instance is associated with a unique `instance_key`. You can use this `instance_key` to manage the instance.

### Creating an instance

To create an instance, you need to send a `POST` request to the `/api/instances/create` endpoint. 

You can include a `instance_key` in the query parameters. If you don't include a `instance_key`, the API will generate a random `instance_key` for you.
 

