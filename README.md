# Ansible Role: Kometa on Docker <!-- omit in toc -->

[![github](https://github.com/organicveggie/ansible.kometa/workflows/Lint/badge.svg)](https://github.com/organicveggie/ansible.kometa/actions)
[![Issues](https://img.shields.io/github/issues/organicveggie/ansible.kometa.svg)](https://github.com/organicveggie/ansible.kometa/issues/)
[![PullRequests](https://img.shields.io/github/issues-pr-closed-raw/organicveggie/ansible.kometa.svg)](https://github.com/organicveggie/ansible.kometa/pulls/)
[![Last commit](https://img.shields.io/github/last-commit/organicveggie/ansible.kometa?logo=github)](https://github.com/organicveggie/ansible.kometa/commits/main)

An [Ansible](https://www.ansible.com/) role to setup and run the
[Kometa](https://kometa.wiki/en/latest//) [Docker](http://www.docker.com)
[container](https://hub.docker.com/r/meisnate12/plex-meta-manager).

## Contents <!-- omit in toc -->

- [Requirements](#requirements)
- [Role Variables](#role-variables)
  - [Container Settings](#container-settings)
  - [Docker volumes and folders](#docker-volumes-and-folders)
  - [Docker Networks](#docker-networks)
- [Dependencies](#dependencies)
- [Example Playbooks](#example-playbooks)
- [License](#license)
- [Author Information](#author-information)

## Requirements

Requires Docker. Reecommended role for Docker installation:
[geerlingguy.docker](https://galaxy.ansible.com/geerlingguy/docker).

## Role Variables

See [defaults/main.yml](defaults/main.yml) for a complete list.

### Container Settings

```yaml
# Name of the Docker container.
kometa_docker_name: "kometa"

# Base name of the Docker image to use for the container.
kometa_docker_image_name: "kometateam/kometa"

# Specific Docker image version to use for the container.
kometa_docker_image_version: "latest"

# TCP port number to expose to handle HTTP traffic.
kometa_docker_web_port: "8181"

# Number of vCPUs to allocate to the container.
kometa_docker_cpus: "1"

# Amount of memory to allocate to the container.
kometa_docker_memory: "512M"

# User ID for the file/directory owner.
kometa_docker_uid: null

# Group ID for the file/directory owner.
kometa_docker_gid: null
```

### Docker volumes and folders

```yaml
# Create and use Docker volumes for storing data. True creates volumes and attaches them to the
# container. False creates folders and bind mounts them to the container.
kometa_docker_use_volumes: true

# Name of the Docker volume to create to store data files. Only used when
# [kometa_docker_use_volumes] is true.
kometa_docker_volume_name: "kometa"

# Directory on filesystem to use for storing data files. Only used when
# [kometa_docker_use_volumes] is false.
kometa_docker_data_dir: "/var/lib/kometa"
```

### Docker Networks

```yaml
# Name of the default Docker network for the container. The container will *always* attach to this
# network. If [kometa_docker_network_create] is true, this is also the name of the network which
# will be created.
kometa_docker_network: "kometa"

# List of additional networks the container should attach to. Elements should be dictionaries like
# https://docs.ansible.com/ansible/latest/collections/community/docker/docker_container_module.html#parameter-networks.
kometa_docker_extra_networks: []

# List of aliases for this container in the default network. These names can be used in the default
# network to reach this container.
kometa_docker_network_aliases: []

# The container’s IPv4 address in the default network. Defaults to using DHCP.
kometa_docker_network_ipv4: null

# The container’s IPv6 address in the default network. Defaults to using DHCP. Only applies if
# IPv6 is enabled in the default network.
kometa_docker_network_ipv6: null

# Create the default Docker network. True creates network and attaches the container to it. False
# does not create the network.
kometa_docker_network_create: false

# Driver to use for the default Docker network for the container. Only used when
# [kometa_docker_network_create] is enabled. See
# https://docs.docker.com/network/#network-drivers for available options.
kometa_docker_network_driver: "bridge"

# Enable IPv6 in the default Docker network for the container. Only used when
# [kometa_docker_network_create] is enabled.
kometa_docker_network_enable_ipv6: "false"

# Restrict external access to the default network. See
# https://docs.docker.com/engine/reference/commandline/network_create/#network-internal-mode.
# Only used when [kometa_docker_network_create] is enabled.
kometa_docker_network_internal: "yes"

# Control the default network's scope. Only used when [kometa_docker_network_create] is enabled.
kometa_docker_network_scope: "local"

# IPv4 subnet for the default network. Only used when [kometa_docker_network_create] is enabled.
kometa_docker_network_subnet: "172.1.1.0/24"

# IPv4 gateway for the default network. Only used when [kometa_docker_network_create] is
# enabled.
kometa_docker_network_gateway: "172.1.1.1"
```

## Dependencies

None.

## Example Playbooks

TODO

## License

[GNU AFFERO GPL](LICENSE)

## Author Information

[Sean Laurent](http://github/organicveggie)
