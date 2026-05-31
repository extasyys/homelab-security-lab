# Homelab Inventory

Sanitized inventory of my current Proxmox homelab.

This file documents the hardware, virtual machines, containers, storage, and networking layout without exposing real IP addresses, credentials, tokens, or sensitive service names.

## Physical Host

| Item | Value |
|---|---|
| Host | Lenovo ThinkCentre M720Q |
| CPU | Intel Core i5-8400T |
| CPU details | 6 cores / 6 threads, 1.70 GHz base, 3.30 GHz turbo, 35 W TDP |
| RAM | 16 GB |
| Storage | 240 GB SSD |
| Extra storage | None |
| UPS | No |
| Hypervisor | Proxmox VE 9.1.1 |
| Install type | Bare metal |

## Network Interfaces

| Interface | Type | Public description |
|---|---|---|
| Onboard NIC | Ethernet | Main Proxmox bridge / management side |
| USB-C to RJ45 adapter | Ethernet | Secondary network bridge |

## Proxmox Network Bridges

| Bridge | Purpose | Notes |
|---|---|---|
| `vmbr0` | Main bridge | Used for main Proxmox networking |
| `vmbr1` | Secondary bridge | Used for secondary network path |

Current notes:

- VLAN-aware bridge mode is not enabled yet.
- Network segmentation is planned for future improvement.
- Real IP addresses are intentionally not published.

## Storage

| Storage | Purpose | Notes |
|---|---|---|
| `local` | Default Proxmox storage | Exact usage still being documented |
| `local-lvm` | VM/container disk storage | Used for virtual disks |

## Containers

| Public name | Type | Purpose | Status |
|---|---|---|---|
| `ct-cloudflared` | LXC | Cloudflare Tunnel connector | Running |
| `ct-discordbot` | LXC | Discord bot workload | Running |

## Virtual Machines

| Public name | Type | Purpose | Status |
|---|---|---|---|
| `vm-ubuntu-server` | QEMU/KVM VM | Minecraft server + WireGuard relay routing | Powered off when not needed |
| `vm-opnsense-firewall` | QEMU/KVM VM | Main home firewall/router | Running |
| `vm-security-lab` | QEMU/KVM VM | Security lab VM | Running |

## External Access Design

| Service | Exposure method | Reason |
|---|---|---|
| Public websites | Cloudflare Tunnel | Avoid direct router port forwarding |
| Minecraft server | WireGuard tunnel to Lithuanian VPS | Avoid exposing residential IP |
| Proxmox UI | Not exposed publicly | Management should stay private |

## Service Summary

| Component | Role |
|---|---|
| Proxmox VE | Main virtualization platform |
| OPNsense VM | Real home firewall/router |
| Cloudflare Tunnel container | Publishes selected web services |
| Ubuntu Server VM | Hosts Minecraft server when needed |
| Lithuanian VPS | Relay endpoint for Minecraft traffic |
| WireGuard | VPN tunnel between VPS and home server |

## Current Security Status

| Area | Status |
|---|---|
| Proxmox firewall | Enabled |
| Router port forwarding | Not used |
| Proxmox 2FA | Not enabled yet |
| Separate admin user | Not configured yet |
| SSH key-based login | Not configured yet |
| SSH password login disabled | No |
| Scheduled backups | Not configured yet |
| Restore testing | Not tested yet |
| VLAN segmentation | Planned |

## Public Documentation Rules

Before publishing screenshots, configs, or notes:

- Remove real public IP addresses
- Remove private IP addresses
- Remove VPN keys
- Remove Cloudflare tokens
- Remove passwords
- Remove exported firewall configs
- Rename sensitive VM names
- Crop or blur screenshots
- Avoid publishing raw Proxmox or OPNsense configuration exports

## Notes

This lab is still evolving. The current priority is to document the existing setup, then improve security basics such as 2FA, SSH hardening, backups, restore testing, and cleaner network segmentation.
