# SVMC-AX51NVME-01

Dedicated server. Hosts the production Minecraft server. NGINX is installed to serve the squaremap. Accessed via reverse proxy through webserver.

## Packages Installed:

- OpenJDK from https://adoptium.net/
- mcrcon from https://github.com/Tiiffi/mcrcon
- letsencrypt from https://certbot.eff.org/instructions?ws=nginx&os=centosrhel8
- Git
- tar
- nginx
- php
- snapd
- mariadb
- mariadb-server

## Users created:

- minecraft /var/minecraft /bin/bash minecraft
- \<all admins\>


## External Firewall:

- 25565 tcp/udp
- 80,443,8192 tcp
- 22 tcp
- 32768-65535 tcp ack|fin
