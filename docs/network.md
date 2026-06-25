# Network Configuration

## Overview

The homelab is connected to the home network and accessed remotely through Tailscale.
Note: Other than the standard ports not all ports are exact in this Doc for security reasons

## Services

| Service | Port |
|----------|------|
| SSH | 22 |
| CasaOS | 80 |
| Jellyfin | 237382 |
| Vaultwarden | Containerized |

## Remote Access

Tailscale is used for encrypted remote connectivity.

Benefits:
- No port forwarding required
- Secure device authentication
- Remote administration
