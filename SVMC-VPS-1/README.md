# SVMC-VPS-1

Cloud server. Hosts website and reverse proxy to map on production Minecraft server.

Website located at /var/minecraft/svmc-website and /var/minecraft/asthonia-website

## Packages Installed:

- letsencrypt from https://certbot.eff.org/instructions?ws=nginx&os=centosrhel8
- Git
- tar
- wget
- nginx
- php
- snapd
- firewalld

## Users created:

- minecraft /var/minecraft /bin/bash (no password) (aka SVMC Bot on Github)
- \<all admins\> (add to "minecraft" group)

## External Firewall:

Standard:
- allow all established tcp (priority 0)
- 443 tcp (priority 1)
- 80 tcp (priority 2)
- 22 tcp (priority 17)
- deny all ipv4 (priority 19)
