# nanobot-docker

Automated Docker image builds for [HKUDS/nanobot](https://github.com/HKUDS/nanobot) — a ultra-lightweight personal AI agent framework.

> This repository tracks upstream releases and publishes ready-to-use Docker images, since the nanobot project does not provide official images.

## Quick Start

```bash
docker run -v ~/.nanobot:/home/nanobot/.nanobot \
  yanickxia/nanobot-docker:latest agent
```

## Images

Images are available on both registries:

| Registry | Image |
|---|---|
| Docker Hub | `yanickxia/nanobot-docker` |
| GitHub Container Registry | `ghcr.io/yanickxia/nanobot-docker` |

Tags follow upstream nanobot release tags (e.g. `v0.1.5`), plus `latest`.

## Configuration

nanobot reads its config from `~/.nanobot/config.json`. Mount this directory into the container:

```bash
# First-time setup (runs interactively)
docker run -it -v ~/.nanobot:/home/nanobot/.nanobot \
  yanickxia/nanobot-docker:latest onboard

# Start the agent
docker run -v ~/.nanobot:/home/nanobot/.nanobot \
  yanickxia/nanobot-docker:latest agent

# Check status
docker run -v ~/.nanobot:/home/nanobot/.nanobot \
  yanickxia/nanobot-docker:latest status
```

## Exposed Port

Port `18790` is used by the nanobot gateway. Map it if needed:

```bash
docker run -p 18790:18790 -v ~/.nanobot:/home/nanobot/.nanobot \
  yanickxia/nanobot-docker:latest agent
```

## How It Works

- GitHub Actions checks the [upstream nanobot releases](https://github.com/HKUDS/nanobot/releases) **every hour**
- If a new tagged release is detected, it clones that exact tag, builds the image, and pushes to both registries
- If there is no new release, the build is skipped
- A `force rebuild` option is available via manual workflow dispatch

## CI Status

[![Build and Push Docker Image](https://github.com/yanickxia/nanobot-docker/actions/workflows/docker-build.yml/badge.svg)](https://github.com/yanickxia/nanobot-docker/actions/workflows/docker-build.yml)

## Links

- [nanobot upstream](https://github.com/HKUDS/nanobot)
- [Docker Hub](https://hub.docker.com/r/yanickxia/nanobot-docker)
- [GitHub Container Registry](https://github.com/yanickxia/nanobot-docker/pkgs/container/nanobot-docker)
