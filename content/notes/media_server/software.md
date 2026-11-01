---
title: Software
publish: true
---

The setup is mostly automated, with manual oversight for dangerous actions.

## Operating System

OS: Rocky Linux 10

Purpose: Run podman containers to self-host applications. See [[software#Applications|Applications]] for more info.

## Applications

All the applications are running in Podman containers and are being managed by systemd.

- Jellyfin
- qBittorrent
- Sonarr
- Radarr 
- Prowlarr

The unit files themselves are in a Github [repo](https://github.com/raycadle/media_server).
There's also a [script](https://github.com/raycadle/media_server/blob/main/setup_streamarr.sh) that *should* setup everything -- it may be broken, ymmv.