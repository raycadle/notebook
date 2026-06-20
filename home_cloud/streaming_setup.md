---
title: Streaming Setup
parent: Home Cloud
---

# Streaming Setup

My streaming setup is fairly simple and automated. It's currently made up of Jellyfin for streaming, qBittorrent for downloading, and the \*arr suite (prowlarr, sonarr, radarr, and lidarr) for finding torrents.

The script that I use is below. I chose to name it `streamarr.sh` to pay homage to the work horses of the setup. I thought about creating a git repo to track changes I make to it, but that seems a bit overkill for something that is only used once every year or longer.

```bash
#!/usr/bin/env bash

PUID=0
PGID=0
TZ=America/Belize
APPS="${HOME}"/apps
ANIME=/mnt/media/anime
SHOWS=/mnt/media/shows
MOVIES=/mnt/media/movies
MUSIC=/mnt/media/music

create_pod () {
  podman pod create \
    --name=streamarr \
    -p 8096:8096 `#jellyfin http` \
    -p 8920:8920 `#jellyfin https` \
    -p 7359:7359/udp `#jellyfin network discovery` \
    -p 1900:1900/udp `#jellyfin DNLA discovery` \
    -p 8080:8080 `#qbittorrent webui` \
    -p 6881:6881 `#qbittorrent extra` \
    -p 6881:6881/udp `#qbittorrent extra` \
    -p 9696:9696 `#prowlarr` \
    -p 8989:8989 `#sonarr` \
    -p 7878:7878 `#radarr` \
    -p 8686:8686 `#lidarr`
}

run_jellyfin () {
  podman run -d \
    --pod=streamarr \
    --name=jellyfin \
    --restart=unless-stopped \
    -e PUID="${PUID}" \
    -e PGID="${PGID}" \
    -e TZ="${TZ}" \
    --device=/dev/dri:/dev/dri \
    -v "${APPS}"/jellyfin/config:/config:Z \
    -v "${SHOWS}":/data/tvshows:z \
    -v "${MOVIES}":/data/movies:z \
    -v "${ANIME}":/data/anime:z \
    -v "${MUSIC}":/data/music:z \
    lscr.io/linuxserver/jellyfin:latest
}

run_qbittorrent () {
  podman run -d \
    --pod=streamarr \
    --name=qbittorrent \
    --restart=unless-stopped \
    -e PUID="${PUID}" \
    -e PGID="${PGID}" \
    -e TZ="${TZ}" \
    -e WEBUI_PORT=8080 \
    -e TORRENTING_PORT=6881 \
    -v "${APPS}"/qbittorrent/config:/config:Z \
    -v "${APPS}"/downloads:/downloads:z \
    lscr.io/linuxserver/qbittorrent:latest
}

run_prowlarr () {
  podman run -d \
    --pod=streamarr \
    --name=prowlarr \
    --restart=unless-stopped \
    -e PUID="${PUID}" \
    -e PGID="${PGID}" \
    -e TZ="${TZ}" \
    -v "${APPS}"/prowlarr/config:/config:Z \
    lscr.io/linuxserver/prowlarr:latest
}

run_sonarr () {
  podman run -d \
    --pod=streamarr \
    --name=sonarr \
    --restart=unless-stopped \
    -e PUID="${PUID}" \
    -e PGID="${PGID}" \
    -e TZ="${TZ}" \
    -v "${APPS}"/sonarr/config:/config:Z \
    -v "${SHOWS}":/tv:z \
    -v "${APPS}"/downloads:/downloads:z \
    lscr.io/linuxserver/sonarr:latest
}

run_radarr () {
  podman run -d \
    --pod=streamarr \
    --name=radarr \
    --restart=unless-stopped \
    -e PUID="${PUID}" \
    -e PGID="${PGID}" \
    -e TZ="${TZ}" \
    -v "${APPS}"/radarr/config:/config:Z \
    -v "${MOVIES}":/movies:z \
    -v "${APPS}"/downloads:/downloads:z \
    lscr.io/linuxserver/radarr:latest
}

run_lidarr () {
  podman run -d \
    --pod=streamarr \
    --name=lidarr \
    --restart=unless-stopped \
    -e PUID="${PUID}" \
    -e PGID="${PGID}" \
    -e TZ="${TZ}" \
    -v "${APPS}"/lidarr/config:/config:Z \
    -v "${MUSIC}":/music:z \
    -v "${APPS}"/downloads:/downloads:z \
    lscr.io/linuxserver/lidarr:latest
}

main () {
  mkdir -p "${APPS}"/downloads
  mkdir -p "${APPS}"/{jellyfin,qbittorrent,prowlarr,sonarr,radarr,lidarr}/config
  create_pod
  run_jellyfin
  run_qbittorrent
  run_prowlarr
  run_sonarr
  run_radarr
  run_lidarr
}

main
```