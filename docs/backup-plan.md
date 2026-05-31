# Backup Plan

Current backup status: not configured yet.

## Planned backup targets

| Target | Priority | Reason |
|---|---|---|
| OPNsense VM | High | Main firewall/router configuration |
| ct-cloudflared | High | Tunnel service configuration |
| ct-discordbot | Medium | Bot workload |
| vm-ubuntu-server | Medium | Minecraft server when active |
| vm-security-lab | Low | Lab VM can be rebuilt |

## Backup goals

- Configure scheduled backups
- Store backups outside the main VM disk storage
- Test at least one restore
- Document restore steps

## Notes

A backup is not finished until restore has been tested.
