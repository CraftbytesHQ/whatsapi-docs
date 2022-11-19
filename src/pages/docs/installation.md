---
title: Installation
description: Installing WhatsAPI on your system
---

There are two ways to run WhatsAPI on your system, either by using the binary directly or by using the Docker image. We recommend using the Docker image as it is easier to manage and update. However, if you are not familiar with Docker, you can use the binary directly. The guide below covers both the methods.

---

## Installing using docker

Docker is a containerization platform that allows you to run applications in isolated containers. It is a very popular platform and is used by many companies. It is also very easy to manage and update. You can learn more about Docker [here](https://www.docker.com/).

### Prerequisites

- Docker
- Docker-compose

### Installing Docker

Docker is available for all major operating systems. You can install it using the following commands.

#### Ubuntu

```bash
sudo apt update && sudo apt upgrade -y
sudo apt install docker.io docker-compose -y

```

#### CentOS

```bash
sudo yum update -y
sudo yum install docker docker-compose -y

```

#### Arch Linux

```bash
sudo pacman -Syu
sudo pacman -S docker docker-compose
```

### Getting config file ready

The config file is a YAML file that contains all the configuration required to run WhatsAPI. You can find the sample config file [here](https://config.whatsapi.net/). You can download the file and edit it as per your requirements. You can also use the [WhatsAPI Config Generator](https://config.whatsapi.net/) to generate the config file.

You might not have to change the `database` section of the config file. You can leave it as it is. However, you will have to change the `credentials` section. You can get your API credentials from the [WhatsAPI Dashboard](https://dashboard.whatsapi.net/).

### Running WhatsAPI

You can run WhatsAPI using the following command.

```bash
docker run --name whatsapi -p 8080:8080 -v /path/to/config.yaml:/app/config.yaml manjit/whatsapi
```

This will start the WhatsAPI container and expose the API on port 8080. You can now access the API using the following URL.

```bash
http://localhost:8080
```

That's it. Your system is now setup with the following components.

- WhatsAPI
- PostgreSQL
- Redis
- SEQ Logging

#### Running in background

You can run WhatsAPI in the background using the following command.

```bash
docker run --name whatsapi -d -p 8080:8080 -v /path/to/config.yaml:/app/config.yaml manjit/whatsapi
```

#### Auto restart

You can also use the following command to run the WhatsAPI container in the background and restart it automatically on system restart.

```bash
docker run --name whatsapi -d --restart=always -p 8080:8080 -v /path/to/config.yaml:/app/config.yaml manjit/whatsapi
```

### Updating WhatsAPI

You can update WhatsAPI using the following command.

```bash
docker pull manjit/whatsapi
```

This will pull the latest version of WhatsAPI. You can then restart the container using the following command.

```bash
docker restart whatsapi
```


## Installing using binary

You can also install WhatsAPI using the binary directly. This is a self-contained executable that can be run on any system. It is also very easy to manage and update. Also having everyting on your server ensures data security and privacy. This guide assumes you are using a Linux system. If you are using Windows, you can use [WSL](https://docs.microsoft.com/en-us/windows/wsl/install-win10) to run the WhatsAPI binary.


### Getting the binary

The latest binary is available only on the [WhatsAPI website](https://whatsapi.netlify.app/). You can download the latest version from there. The binary is available for both 32-bit and 64-bit systems. You can download the one that suits your system.

```shell
wget https://whatsapi.netlify.app/whatsapi
```

With this, you are halfway through. Now you need to setup the configuration file. This is a very simple process.

### Getting config file ready

The config file is a YAML file that contains all the configuration required to run WhatsAPI. You can find the sample config file [here](https://config.whatsapi.net/). You can download the file and edit it as per your requirements. You can also use the [WhatsAPI Config Generator](https://config.whatsapi.net/) to generate the config file.

### Setup systemd service

You can use systemd to run the WhatsAPI binary as a service. This will ensure that the WhatsAPI binary is always running. You can use the following command to create a new service file.

```shell
sudo nano /etc/systemd/system/whatsapi.service
```

Copy the following content into the file and save it.

```ini  
[Unit]
Description=WhatsAPI
After=network.target

[Service]
Type=simple
User=root
WorkingDirectory=/root
ExecStart=/root/whatsapi
Restart=always

[Install]
WantedBy=multi-user.target
```

Remember to change the `WorkingDirectory` and `ExecStart` to the correct path. You can now start the service using the following command.

```shell
sudo systemctl start whatsapi
```

You can check the status of the service using the following command.

```shell
sudo systemctl status whatsapi
```

You can also enable the service to start automatically on system restart.

```shell
sudo systemctl enable whatsapi
```

### Updating WhatsAPI

You can update WhatsAPI using the following command.

```shell
wget https://whatsapi.netlify.app/whatsapi
```

This will download the latest version of WhatsAPI. You can then restart the service using the following command.

```shell
sudo systemctl restart whatsapi
```
