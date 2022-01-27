# SVMC-AX51NVME-01

Dedicated server. Hosts the production Minecraft server.

NGINX is installed to serve the squaremap (port 8080). Accessed via reverse proxy through webserver. HTTPS is enabled via cert generated with OpenSSL:

`sudo openssl req -newkey rsa:2048 -x509 -sha256 -days 730 -nodes -out <ip.crt> -keyout <ip.key>`

Minecraft server located at /var/minecraft/server

MCRCON located at /var/minecraft/mcrcon

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
- openssl

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

GAME:
- 25565

Standard:
- 25565 tcp (priority 0)
- 8080 tcp (priority 1)
- 8192 tcp (priority 2)
- allow all established tcp (priority 11)
- allow all syn tcp (priority 12)
- 22 tcp (priority 18)
- deny all tcp (priotiy 19)
