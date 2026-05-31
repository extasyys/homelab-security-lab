# Homelab Security Lab

![Status](https://img.shields.io/badge/status-active-blue)
![Lab](https://img.shields.io/badge/lab-Proxmox-orange)
![Focus](https://img.shields.io/badge/focus-cybersecurity-green)

Small x86-based cybersecurity homelab running on a Lenovo ThinkCentre M720Q with Proxmox VE.

The goal of this lab is to learn practical networking, virtualization, firewalling, tunneling, service isolation, and basic infrastructure security using real systems.

## Documentation

- [Inventory](docs/inventory.md)
- [Network topology](docs/network-topology.md)
- [Security roadmap](docs/security-roadmap.md)


## Current setup

| Area | Technology |
|---|---|
| Hypervisor | Proxmox VE 9.1.1 |
| CPU | Intel Core i5-8400T, 6C/6T, 1.70–3.30 GHz, 35 W TDP |
| Host | Lenovo ThinkCentre M720Q |
| RAM | 16 GB |
| Storage | 240 GB SSD |
| Network | 1x onboard NIC + 1x USB-C to RJ45 adapter |
| Firewall / routing | OPNsense VM |
| Containers | LXC |
| Virtual machines | QEMU/KVM |
| Tunnel access | Cloudflare Tunnel |
| Game server relay | WireGuard VPN to external Lithuanian VPS |

## Current services

| Public name | Type | Purpose |
|---|---|---|
| `ct-cloudflared` | LXC | Cloudflare Tunnel connector for selected public web services |
| `ct-discordbot` | LXC | Lightweight Discord bot workload |
| `vm-ubuntu-server` | VM | Minecraft server with WireGuard VPS relay |
| `vm-opnsense-firewall` | VM | Main home firewall/router |
| `vm-security-lab` | VM | Security lab VM, sanitized public name |

## Network summary

The Proxmox host sits behind the main ASUS router and runs OPNsense as the real home firewall/router.

External exposure is handled without router port forwarding:

- Cloudflare Tunnel for selected websites
- WireGuard tunnel to a Lithuanian VPS for Minecraft server traffic

## What this repo documents

- Proxmox host inventory
- VM and container layout
- Network topology
- External access design
- Current hardening status
- Security improvement roadmap

## Security note

This repository does not include:

- real public IP addresses
- private IP addresses
- VPN credentials
- Cloudflare tokens
- exported firewall configs
- raw Proxmox screenshots
- SSH keys
- passwords
- sensitive service names
