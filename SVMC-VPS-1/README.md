# SVMC-CPX21-01

Cloud server. Hosts website and reverse proxy to map on production Minecraft server.

Website located at /var/minecraft/website

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
- 443 tcp (priority 0)
- 80 tcp (priority 1)
- allow all established tcp (priority 11)
- 22 tcp (priority 18)
- deny all tcp (priority 19)
