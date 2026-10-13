# docker-homelab - Ubuntu Linux Server

# Project Overview
This repository documents my experience deploying, configuring, and maintaining containerized applications on a personal Ubuntu Linux server.

The project was developed to gain practical experience in Linux system administration, containerization, networking, persistent storage, and infrastructure monitoring.

My homelab runs multiple self-hosted applications using Docker and Docker Compose, allowing me to manage media, music, photos, and system monitoring services from a single physical server.

# Hardware Infastructure

| Component | Specifications |
|---|---|
| Server | HP ProDesk 405 G4 DM |
| CPU | AMD Ryzen 5 PRO 2400GE |
| RAM | 16 GB |
| Operating System | Ubuntu 22.04 LTS |
| Primary Storage | 1 TB SSD |
| External Storage | 4 TB HDD |
| Containerization | Docker Engine + Docker Compose |

# Deployed Applications

| Application | Purpose | Containers |
|---|---|---:|
| Jellyfin | Self-hosted media streaming | 1 |
| Navidrome | Self-hosted music streaming | 1 |
| Immich | Photo and video management | 4 |
| Prometheus | Infrastructure metrics | 1 |
| Grafana | Monitoring dashboards | 1 |
| **Total** | **4 Docker Compose projects** | **8** |

*Deployment note:** The table describes applications I've worked with in the Ubuntu homelab. It does not assert that every application runs as a Docker container. Each deployment's exact installation method and current status should be verified before adding its configuration.

## What this project demonstrates

- Deploying and maintaining self-hosted services on Linux
- Inspecting Docker containers, images, networks, and volumes
- Using Docker Compose to describe application stacks
- Reading logs and investigating failed containers
- Understanding bind mounts, persistent data, and port mappings
- Monitoring CPU, memory, storage, and application availability
- Keeping sensitive configuration out of public repositories

# Repository structure

```text
docker-homelab/
├── README.md
├── .gitignore
├── docs/
│   ├── installation.md
│   ├── commands.md
│   ├── networking-and-storage.md
│   └── troubleshooting.md
├── compose/
│   ├── README.md
│   └── example-compose.yaml
├── scripts/
│   └── docker-health-check.sh
└── screenshots/
    └── README.md
```

## Verified service deep dives

- [Jellyfin Compose deployment](docs/jellyfin-compose.md) — bind mounts, media directories, render device, ports, and restart behavior.
- [Sanitized Jellyfin Compose example](compose/jellyfin/compose.yaml) — adapted for safe sharing; not a verbatim production export.

## Quick start

1. Follow [Docker installation](docs/installation.md) for Ubuntu.
2. Learn everyday commands in [Docker commands](docs/commands.md).
3. Review [networking and storage](docs/networking-and-storage.md).
4. Test the safe sample stack in [`compose/`](compose/README.md).
5. Use the [health-check script](scripts/docker-health-check.sh) to inspect the host.

## Real troubleshooting experience

While deploying Open WebUI with Ollama, I encountered container startup issues and later experienced slow or freezing responses. I investigated service state, connectivity, and the limitations of running local AI workloads on modest hardware. See [troubleshooting](docs/troubleshooting.md) for a reproducible diagnostic workflow. I don't include fabricated benchmark results or claim a definitive root cause that I haven't verified.

## Next improvements

- [ ] Add screenshots from my actual Docker host (with sensitive information removed)
- [ ] Document the exact Docker Compose files used for each confirmed container deployment
- [ ] Add a service inventory with versions and deployment methods
- [ ] Document backups and restore tests for persistent data
- [ ] Add measured CPU/RAM usage and monitoring screenshots

## Security and privacy

Never commit `.env` files, tokens, passwords, personal media, photo libraries, private keys, or full unredacted Docker inspect outputs. Bind services to loopback when public LAN access is unnecessary, and avoid forwarding ports to the internet without a clear need.

## Learning goals

This is an evolving, hands-on project intended to develop skills relevant to Linux system administration, infrastructure operations, and DevOps fundamentals.
