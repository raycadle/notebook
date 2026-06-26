---
title: Services and Daemons
parent: Linux
---

# Services and Daemons

## Reload systemd daemon

```bash
systemctl reload-daemon
```

## Check running services

```bash
systemctl list-units --type-service
```

## List all services

```bash
systemctl --all
```

## Check status of services

```bash
systemctl status sshd.service
```

## Stop a service

```bash
systemctl stop sshd.service
```

## Start a service

```bash
systemctl start sshd.service
```

## Check if a service is enabled to run at boot

```bash
systemctl is-enabled sshd.service
```

## Enable a service to start at boot

```bash
systemctl enable sshd.service
```

## Enable a service to start at boot and start the service now

```bash
systemctl enable --now sshd.service
```

## Disable a service from start at boot

```bash
systemctl disable sshd.service
```

## Disable a service from start at boot and stop the service now

```bash
systemctl disable --now sshd.service
```

## Restart a service

```bash
systemctl restart sshd.service
```

## Enable a service for a current user and start the service now

```bash
systemctl --user enable --now sshd.service
```

## Disable a service for a current user and stop the service now

```bash
systemctl --user disable --now sshd.service
```
