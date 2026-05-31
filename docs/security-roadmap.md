# Security Roadmap

This file tracks the current hardening status of the homelab.

The goal is to keep the lab honest: document what is already done, what is missing, and what should be improved next.

## Current status

| Area | Status | Notes |
|---|---|---|
| Proxmox firewall | Enabled | Basic protection enabled |
| Router port forwarding | Not used | External access avoids direct port forwarding |
| Cloudflare Tunnel | In use | Used for selected web services |
| WireGuard VPS relay | In use | Used for Minecraft server traffic |
| Proxmox 2FA | Not enabled | Planned |
| Separate admin user | Not configured | Planned |
| SSH key-based login | Not configured | Planned |
| SSH password login disabled | No | Planned |
| Scheduled backups | Not configured | Planned |
| Restore testing | Not tested | Planned |
| UPS | Not available | Optional future improvement |
| VLAN-aware bridges | Not enabled | Planned / under review |

## Priority improvements

### 1. Enable Proxmox 2FA

Reason: protects the Proxmox management interface if credentials are leaked.

### 2. Create a separate admin user

Reason: daily administration should not depend only on the root account.

### 3. Harden SSH

Planned changes:

- enable key-based SSH login
- disable password-based SSH login
- restrict SSH access where possible

### 4. Configure scheduled backups

Planned backup targets:

- OPNsense VM
- cloudflared container
- Discord bot container
- Ubuntu server VM when Minecraft server is active

### 5. Test restore process

Backups are not complete until restore has been tested. Otherwise it is just digital optimism.

### 6. Review network segmentation

Current bridges are not VLAN-aware.

Planned work:

- review VLAN design
- separate management, services, and lab workloads where possible
- avoid overcomplicating the setup before basic backups and SSH hardening are done

## Public documentation rules

Before publishing anything:

- [ ] Remove real public IP addresses
- [ ] Remove private IP addresses
- [ ] Remove Cloudflare tunnel tokens
- [ ] Remove WireGuard keys
- [ ] Remove VPS IP if not intentionally public
- [ ] Remove raw firewall exports
- [ ] Rename sensitive VM names
- [ ] Crop or blur screenshots
- [ ] Avoid publishing security-sensitive lab details
