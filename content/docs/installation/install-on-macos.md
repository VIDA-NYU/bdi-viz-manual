---
weight: 300
title: "Install on MacOS"
description: "Step-by-step guide for installing and configuring BDIViz on MacOS(ARM64) systems"
icon: "apple"
date: "2025-04-19T13:38:17-04:00"
lastmod: "2025-04-21T11:00:00-04:00"
draft: false
toc: true
---

## Prerequisites

Before setting up BDIViz on your Mac, ensure your system meets the following requirements:

- Mac computer with Apple Silicon (M1, M2, M3, etc.) – ARM64 architecture
- macOS 12.0 Monterey or later
- Docker Desktop for Mac (ARM64 version)
- At least 4GB of RAM and 10GB of free disk space
- Internet connection to pull the Docker image

---

## Install Docker Desktop for Mac

1. Download Docker Desktop for Mac (Apple Silicon):
   👉 [https://www.docker.com/products/docker-desktop/](https://www.docker.com/products/docker-desktop/)

2. Open the downloaded `.dmg` file and drag Docker to your Applications folder.

3. Launch Docker Desktop from Spotlight or Applications.

4. Grant permissions if prompted and wait for Docker to start (you should see the Docker icon in the menu bar).

5. Open Terminal and verify installation:

```bash
docker --version
```

You should see an output like:
```nginx
Docker version 24.0.0, build xxxxxxxx
```

## Run BDIViz Using Docker

### 1. Pull the Docker image
```bash
docker pull edenwu/bdi-viz-react:arm64
```

### 2. Run the container
```bash
docker run -d \
  --name bdiviz \
  -p 3000:3000 \
  edenwu/bdi-viz-react:arm64
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