# SVMC-CPX21-02

Cloud server. Hosts test server, identical to production Minecraft server. Accessed via IP.

Minecraft server located at /var/minecraft/server

MCRCON located at /var/minecraft/mcrcon

Java is located at /usr/java/\<version\>

## Packages Installed:

- jdk-17.0.1+12 Temurin JRE from https://adoptium.net/
- mcrcon from https://github.com/Tiiffi/mcrcon
- letsencrypt from https://certbot.eff.org/instructions?ws=nginx&os=centosrhel8
- Git
- tar
- firewalld
- wget
- nginx
- php
- snapd
- mariadb-server

## Users created:

- minecraft /var/minecraft /bin/bash (no password) (aka SVMC Bot on Github)
- \<all admins\> (add to "minecraft" group)

## Path variables added:

- /var/minecraft/mcrcon
- /usr/java/jdk-17.0.1+12/bin

## External Firewall:

- 25565 tcp/udp
- 8080,8192 tcp
- 22 tcp
- all outbound traffic
