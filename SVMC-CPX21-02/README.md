# SVMC-CPX21-02

Cloud server. Hosts test server, identical to production Minecraft server. Accessed via IP.

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

## Users created:

- minecraft /var/minecraft /bin/bash (no password) (aka SVMC Bot on Github)
- \<all admins\> (add to "minecraft" group)

## MariaDB Setup:

CREATE DATABASE aurelium;
CREATE DATABASE coreprotect;
CREATE DATABASE litebans;
CREATE DATABASE luckperms;
CREATE DATABASE lwc;
CREATE USER 'aurelium'@localhost IDENTIFIED BY 'NHCwp2D6NU9Z8cX5';
CREATE USER 'coreprotect'@localhost IDENTIFIED BY '3ZBwCESb6C65Rpda';
CREATE USER 'litebans'@localhost IDENTIFIED BY 'TA6gFmSbUqj8WexX';
CREATE USER 'luckperms'@localhost IDENTIFIED BY 'D744wXcSQr6hSwYQ';
CREATE USER 'lwc'@localhost IDENTIFIED BY 'CyT5Q8vfyppjXNSY';
GRANT ALL PRIVILEGES ON aurelium.* TO 'aurelium'@localhost;
GRANT ALL PRIVILEGES ON coreprotect.* TO 'coreprotect'@localhost;
GRANT ALL PRIVILEGES ON litebans.* TO 'litebans'@localhost;
GRANT ALL PRIVILEGES ON luckperms.* TO 'luckperms'@localhost;
GRANT ALL PRIVILEGES ON lwc.* TO 'lwc'@localhost;
FLUSH PRIVILEGES;

## External Firewall:

Standard:
- 25565 udp (priority 0)
- 25565 tcp (priority 1)
- 8080 tcp (priority 2)
- 8192 tcp (priority 3)
- allow all established tcp (priority 11)
- allow all syn tcp (priority 12)
- 22 tcp (priority 17)
- refuse all udp (priority 18)
- refuse all tcp (priotiy 19)
