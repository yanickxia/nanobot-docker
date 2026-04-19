# nanobot-docker

Automated Docker image builds for [HKUDS/nanobot](https://github.com/HKUDS/nanobot), a lightweight personal AI agent.

## Image

```
ghcr.io/yanickxia/nanobot-docker:latest
```

## Usage

```bash
docker run -v ~/.nanobot:/home/nanobot/.nanobot ghcr.io/yanickxia/nanobot-docker:latest agent
```

## How it works

- GitHub Actions checks the upstream `HKUDS/nanobot` commit SHA **every hour**
- If the source has changed, it clones the repo, builds the image, and pushes to ghcr.io
- If there are no changes, the build is skipped
- Image tags: `latest` and the upstream commit SHA

## CI Status

[![Build and Push Docker Image](https://github.com/yanickxia/nanobot-docker/actions/workflows/docker-build.yml/badge.svg)](https://github.com/yanickxia/nanobot-docker/actions/workflows/docker-build.yml)
