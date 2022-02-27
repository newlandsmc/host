# SVMC-GAME-1

Dedicated server. Hosts the production Minecraft server.

NGINX is installed to serve the squaremap (port 8080). Accessed via reverse proxy through webserver. HTTPS is enabled via cert generated with OpenSSL:

`sudo openssl req -newkey rsa:2048 -x509 -sha256 -days 730 -nodes -out <ip.crt> -keyout <ip.key>`

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
- openssl
- python3-devel
- python3-pip
- cargo
- nbted from https://github.com/C4K3/nbted

## Users created:

- minecraft /var/minecraft /bin/bash (no password) (aka SVMC Bot on Github)
- \<all admins\> (add to "minecraft" group)
- root and default user have no password (passwd -dl \<username\>)

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

## Setup backups to S3 with:

https://support.us.ovhcloud.com/hc/en-us/articles/4408821185043-Getting-Started-with-the-Swift-S3-API

## External Firewall:

GAME:
- 25565
- 19132

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
