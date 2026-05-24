---
title: Podman & Systemd
parent: Linux Notes
---

# Podman & Systemd

Systemd can be used to start and stop containers at boot and shutdown, respectively. This creates a scenario where no intervention is needed on a system reboot.

Before proceeding, be sure to enable linger for whichever user will be running the containers.

- Enable `linger` for the user that will run the container.

```bash
loginctl enable-linger $USER
```

- Create `~/.config/systemd/user` to keep the user systemd unit files.

```bash
mkdir -p ~/.config/systemd/user
```

## Creating systemd unit files for podman containers

1. Run the container with all the mounts, ports, and env variables needed.

2. Generate systemd unit file using `podman generate` command.

```bash
podman generate systemd --new --files --name $container_name
```

3. Stop and remove the container.

4. Move the service unit file to `~/.config/systemd/user`.

```bash
mv -Z container-$container_name.service ~/.config/systemd/user/
```

5. Reload the systemd daemon.

```bash
systemctl --user reload-daemon
```

6. Enable and start the container using `systemctl`.

```bash
systemctl --user enable --now container-$container_name.service
```

## Creating systemd unit files for podman pods

Creating a systemd unit file for a pod is the same as with a container. The only difference is that a systemd unit file will be created for each container that is a part of the pod.

1. Run the pod and containers with all the mounts, ports, and env variables needed.

2. Generate service file using `podman generate` command.

```bash
podman generate systemd --new --files --name $pod_name
```

3. Stop and remove the pod and containers.

4. Move all the unit files to `~/.config/systemd/user/`

```bash
mv -Z pod-$pod_name.service container-* ~/.config/
```

5. Reload the systemd daemon.

```bash
systemctl --user reload-daemon
```

6. Enable and start the pod using `systemctl`. This will start all dependent containers as well.

```bash
systemctl --user enable --now pod-$pod_name.service
```
