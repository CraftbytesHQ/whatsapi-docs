---
title: Configuration
description: Configuring WhatsAPI to suit your needs
---

WhatsAPI uses a YAML file to store all the configuration required to run the API. You can find the sample config file [here](https://config.whatsapi.net/). 

---

## Config file

Here is the sample config file.

```yaml
database:
  host: postgres
  port: 5434
  user: root
  password: root
  database: whatsapi

defaults:
  webhook_url: http://localhost:8080/webhook
  send_webhook: true
  client_name: "My Client"
  browser: "chrome"
  http_port: 8083
  socket_port: 8084
  metrics_url: my_metrics
  max_log_size: 10 # in MB

environment: production

credentials:
  key: "my-api-key"
  secret: "my-api-secret"

tls_config:
  https_enabled: true
  hosts:
    - "localhost"

tokens: ["token1", "token2"]
```

### Understanding the config file

The config file is divided into 6 sections.

#### Database
This section contains the database configuration. You can leave this section as it is if you are using the WhatsAPI Docker image. The Docker image uses PostgreSQL as the database. You can change the database configuration if you are using a different database.

#### Defaults
This section contains the default values for the API. You can change these values as per your requirements. The following are the default values.

```yaml
defaults:
  webhook_url: http://localhost:8080/webhook
  send_webhook: true

  client_name: "My Client"
  browser: "chrome"

  http_port: 8083
  socket_port: 8084

  metrics_url: my_metrics

  max_log_size: 10 # in MB
```

Here is the description of each field.

| Field | Description |
| --- | --- |
| webhook_url | The URL to which the webhook will be sent. |
| send_webhook | Whether to send webhook or not. |
| client_name | The name of the visible to user in WhatsApp. |
| browser | The browser name visible in WhatsApp. |
| http_port | The port on which the HTTP server will run. |
| socket_port | The port on which the socket server will run. |
| metrics_url | The URL on which the metrics will be exposed. |
| max_log_size | The maximum size of the log file. |

#### Environment
This section contains the environment name. You can set this to `production` or `development`. This will be used to set the log level.

#### Credentials
This section contains the API credentials. You can get your API credentials from the [WhatsAPI Dashboard](https://dashboard.whatsapi.net/).

#### TLS Config
This section contains the TLS configuration. You can enable HTTPS by setting `https_enabled` to `true`. You can also add the hostnames to the `hosts` array.

#### Tokens
This section contains the API tokens. You can add multiple tokens to this array. You can use these tokens to authenticate the API requests.


