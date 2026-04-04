# Demo: SSH Certificate Authentication

The content in this repository goes with teh demo posted to my youtube channel.

- TOD: Add URL

The demo covers OpenSSH authentication using SSH CA signed certificates.

## Repo Contents

### Demo Script

The [Demo.md](Demo.md) file contains the video "script" from the demo as well
as the commands I copy/paste to create the demonstration.

### Container Files

The `containers` sub-directory contains two Container files that can be used to
build the containers I used during the demo for your own testing.

These containers have been thoroughly tested in `podman` but running them in
docker may require adding the `--privileged` flag for systemd support to work.

This flag has not required in Podman based testing

**Building:**

```bash
# Build the container with defaults; more build options in container file header
#
# AlmaLinux 10
podman build -t systemd-almalinux:latest -t systemd-almalinux:10 -f Containerfile.almalinux .

# Debian 13
podman build -t systemd-debian:latest -t systemd-debian:13 -f Containerfile.debian .
```

**Usage:**

```bash
# Start a systemd container named test01 daemonized
podman run -d --name test01 --hostname test01 systemd-almalinux:10

# Launch a Bash shell into the container
podman exec -it test01 bash
```
