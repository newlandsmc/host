# SVMC-VPS-2

Cloud server. Hosts test server, identical to production Minecraft server. Accessed via IP.

Minecraft server located at /var/minecraft/server

mcrcon located at /var/minecraft/mcrcon

nbted located at /var/minecraft/nbted

Java is located at /usr/java/\<version\>

## Packages Installed:

- jdk-17.0.1+12 Temurin JRE from https://adoptium.net/
- mcrcon from https://github.com/Tiiffi/mcrcon
- Git
- tar
- firewalld
- wget
- nginx
- php
- snapd
- mariadb-server
- cargo
- nbted from https://github.com/C4K3/nbted

## Users created:

- minecraft /var/minecraft /bin/bash (no password) (aka SVMC Bot on Github)
- \<all admins\> (add to "minecraft" group)

## MariaDB Setup:

```
CREATE DATABASE aurelium;
CREATE DATABASE coreprotect;
CREATE DATABASE litebans;
CREATE DATABASE luckperms;
CREATE DATABASE lands;
CREATE USER 'aurelium'@localhost IDENTIFIED BY 'NHCwp2D6NU9Z8cX5';
CREATE USER 'coreprotect'@localhost IDENTIFIED BY '3ZBwCESb6C65Rpda';
CREATE USER 'litebans'@localhost IDENTIFIED BY 'TA6gFmSbUqj8WexX';
CREATE USER 'luckperms'@localhost IDENTIFIED BY 'D744wXcSQr6hSwYQ';
CREATE USER 'lands'@localhost IDENTIFIED BY 'eTdpfCe8nG6KrYTZ';
GRANT ALL PRIVILEGES ON aurelium.* TO 'aurelium'@localhost;
GRANT ALL PRIVILEGES ON coreprotect.* TO 'coreprotect'@localhost;
GRANT ALL PRIVILEGES ON litebans.* TO 'litebans'@localhost;
GRANT ALL PRIVILEGES ON luckperms.* TO 'luckperms'@localhost;
GRANT ALL PRIVILEGES ON lands.* TO 'lands'@localhost;
FLUSH PRIVILEGES;
```

## External Firewall:

Standard:
- allow all established tcp (priority 0)
- 25565 udp (priority 1)
- 25565 tcp (priority 2)
- 19132 udp (priority 3)
- 8080 tcp (priority 4)
- 8192 tcp (priority 5)
- 25575 from 54.87.231.232 (priority 13)
- 25575 from 18.209.80.3 (priority 14)
- fragments from 54.87.231.232 (priority 15)
- fragments from 18.209.80.3 (priority 16)
- 22 tcp (priority 17)
- deny all ipv4 (priotiy 19)
