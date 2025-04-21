---
weight: 200
title: "Install on Linux/Unix"
description: "Step-by-step guide for installing and configuring BDIViz on Linux and Unix-based systems"
icon: "smart_toy"
date: "2025-04-19T13:38:17-04:00"
lastmod: "2025-04-19T13:38:17-04:00"
draft: false
toc: true
---

## Prerequisites

Before installing BDIViz on your Linux system, ensure you have the following prerequisites:

- A Linux distribution (Ubuntu, Debian, CentOS, etc.) with amd64 architecture
- Docker Engine installed and running (version 19.03 or later)
- At least 4GB of RAM and 10GB of free disk space
- Internet connection to pull the Docker image

## Install Docker (if not already installed)

If you don't have Docker installed, follow these steps to install it:


{{< tabs tabTotal="3">}}
{{% tab tabName="Ubuntu/Debian" %}}


```bash
sudo apt update
sudo apt install \
    ca-certificates \
    curl \
    gnupg \
    lsb-release

sudo mkdir -p /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | \
    sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg

echo \
  "deb [arch=$(dpkg --print-architecture) \
  signed-by=/etc/apt/keyrings/docker.gpg] \
  https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

sudo apt update
sudo apt install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

sudo systemctl enable docker
sudo systemctl start docker

```

{{% /tab %}}
{{% tab tabName="CentOS/RHEL" %}}

```bash
sudo yum install -y yum-utils
sudo yum-config-manager \
    --add-repo https://download.docker.com/linux/centos/docker-ce.repo
sudo yum install docker-ce docker-ce-cli containerd.io docker-compose-plugin

sudo systemctl enable docker
sudo systemctl start docker
```

{{% /tab %}}
{{% tab tabName="Arch Linux" %}}

```bash
sudo pacman -Syu
sudo pacman -S docker
sudo systemctl enable docker
sudo systemctl start docker
```

{{% /tab %}}
{{< /tabs >}}


## Run BDIViz Using Docker

Once Docker is installed and running, follow these steps to run BDIViz using the **edenwu/bdi-viz-react:amd64** image:

### 1. Pull the Docker image

```bash
docker pull edenwu/bdi-viz-react:amd64
```

### 2. Run the container

```bash
docker run -d \
  --name bdiviz \
  -p 3000:3000 \
  edenwu/bdi-viz-react:amd64
```

This will start the BDIViz container in detached mode and expose the web application at http://localhost:3000.


### 3. Verify the container is running
You can verify the container is up using:

```bash
docker ps
```

If everything is working correctly, you should see ```bdiviz``` listed in the output.

### 4. Stop the container
When you're done, you can stop the container with:

```bash
docker stop bdiviz
```

And if needed, remove it:

```bash
docker rm bdiviz
```

### Note

- Make sure port ```3000``` is available on your host machine.
- You can bind-mount local volumes or customize environment variables for advanced use (e.g., persistent storage, configuration injection).
- To update the image, simply pull the latest tag again and restart the container:
  ```bash
  docker pull edenwu/bdi-viz-react:amd64
  docker stop bdiviz && docker rm bdiviz
  docker run -d --name bdiviz -p 3000:3000 edenwu/bdi-viz-react:amd64
  ```


## Troubleshooting
- **Port already in use?** Try using a different port:
  ```bash
  docker run -d --name bdiviz-mac -p 8080:3000 edenwu/bdi-viz-react:arm64
  ```
  Then access it at http://localhost:8080.
- **Docker daemon not running?** Open Docker Desktop and make sure it's active.
- **Still stuck?** Feel free to reach out or open an issue on the [GitHub repository](https://github.com/VIDA-NYU/bdi-viz-react/issues).