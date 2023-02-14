# SVMC-VPS-1

Cloud server. Hosts website, Discord bot, and reverse proxy to map on production Minecraft server.

Website located at /var/minecraft/svmc-website and /var/minecraft/asthonia-website and /var/minecraft/khavalon-website

Discord bot located at /var/minecraft/discord-bot

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
