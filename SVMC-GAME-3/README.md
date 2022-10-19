# SVMC-GAME-3

Dedicated server. Hosts the production servers.

NGINX is installed to serve the squaremap (port 8080). Accessed via reverse proxy through webserver. HTTPS is enabled via cert generated with OpenSSL:

`sudo openssl req -newkey rsa:2048 -x509 -sha256 -days 730 -nodes -out <ip.crt> -keyout <ip.key>`

Minecraft servers located at /var/minecraft/

mcrcon located at /var/minecraft/mcrcon

~~nbted located at /var/minecraft/nbted~~

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
- snapd from https://snapcraft.io/docs/installing-snap-on-rocky
- mariadb-server
- openssl
- python3-devel
- python3-pip
- ~~cargo~~
- ~~nbted from https://github.com/C4K3/nbted~~

## Users created:

- minecraft /var/minecraft /bin/bash (add to "systemd-journal" group) (no password) (aka SVMC Bot on Github)
- \<all admins\> (add to "minecraft" group)
- root and default user have no password (passwd -dl \<username\>)

## MariaDB Setup:

```
CREATE DATABASE khavalon_aurelium;
CREATE DATABASE khavalon_coreprotect;
CREATE DATABASE khavalon_gpdata;
CREATE DATABASE asthonia_aurelium;
CREATE DATABASE asthonia_coreprotect;
CREATE DATABASE asthonia_gpdata;
CREATE DATABASE litebans;
CREATE DATABASE luckperms;
CREATE DATABASE creative_plotsquared;
CREATE DATABASE creative_coreprotect;
CREATE DATABASE hardline_aurelium;
CREATE DATABASE hardline_luckperms;
CREATE DATABASE hardline_coreprotect;
CREATE DATABASE premiumvanish;
CREATE DATABASE nickname;
CREATE USER 'aurelium'@localhost IDENTIFIED BY 'NHCwp2D6NU9Z8cX5';
CREATE USER 'coreprotect'@localhost IDENTIFIED BY '3ZBwCESb6C65Rpda';
CREATE USER 'litebans'@localhost IDENTIFIED BY 'TA6gFmSbUqj8WexX';
CREATE USER 'luckperms'@localhost IDENTIFIED BY 'D744wXcSQr6hSwYQ';
CREATE USER 'griefprevention'@localhost IDENTIFIED BY 'NYBXJw9K9PhbeZkT';
CREATE USER 'plotsquared'@localhost IDENTIFIED BY 'Cy34cS4mWpdJ62X8';
CREATE USER 'premiumvanish'@localhost IDENTIFIED BY 'p9td448Rmn46jY36';
CREATE USER 'nickname'@localhost IDENTIFIED BY 'iE0vxIkXVlCe9Ue4';
GRANT ALL PRIVILEGES ON khavalon_aurelium.* TO 'aurelium'@localhost;
GRANT ALL PRIVILEGES ON khavalon_coreprotect.* TO 'coreprotect'@localhost;
GRANT ALL PRIVILEGES ON khavalon_gpdata.* TO 'griefprevention'@localhost;
GRANT ALL PRIVILEGES ON asthonia_aurelium.* TO 'aurelium'@localhost;
GRANT ALL PRIVILEGES ON asthonia_coreprotect.* TO 'coreprotect'@localhost;
GRANT ALL PRIVILEGES ON asthonia_gpdata.* TO 'griefprevention'@localhost;
GRANT ALL PRIVILEGES ON litebans.* TO 'litebans'@localhost;
GRANT ALL PRIVILEGES ON luckperms.* TO 'luckperms'@localhost;
GRANT ALL PRIVILEGES ON creative_plotsquared.* TO 'plotsquared'@localhost;
GRANT ALL PRIVILEGES ON creative_coreprotect.* TO 'coreprotect'@localhost;
GRANT ALL PRIVILEGES ON hardline_aurelium.* TO 'aurelium'@localhost;
GRANT ALL PRIVILEGES ON hardline_coreprotect.* TO 'coreprotect'@localhost;
GRANT ALL PRIVILEGES ON hardline_luckperms.* TO 'luckperms'@localhost;
GRANT ALL PRIVILEGES ON premiumvanish.* TO 'premiumvanish'@localhost;
GRANT ALL PRIVILEGES ON nickname.* TO 'nickname'@localhost;
FLUSH PRIVILEGES;
```

## Setup backups to S3 with:

https://support.us.ovhcloud.com/hc/en-us/articles/4408821185043-Getting-Started-with-the-Swift-S3-API

.aws folder will be under root. backup script will run as root.

## Failover IPs:

/30 group purchased

```
ip addr add 147.135.3.152/32 dev enp1s0f0
ip addr add 147.135.3.153/32 dev enp1s0f0
ip addr add 147.135.3.154/32 dev enp1s0f0
ip addr add 147.135.3.155/32 dev enp1s0f0
```

## External Firewall:

Main IP:
- allow all established tcp (priority 0)
- 25565 udp (priority 1)
- 25565 tcp (priority 2)
- 19132 udp (priority 3)
- 8192 tcp (priority 4)
- allow all icmp (priority 11)
- 22 tcp (priority 12)
- 25576 from 54.87.231.232 (priority 13)
- 25577 from 54.87.231.232 (priority 14)
- 25576 from 18.209.80.3 (priority 15)
- 25577 from 18.209.80.3 (priority 16)
- fragments from 54.87.231.232 (priority 17)
- fragments from 18.209.80.3 (priority 18)
- deny all ipv4 (priotiy 19)

Failover IPs:
- allow all established tcp (priority 0)
- 25565 udp (priority 1)
- 25565 tcp (priority 2)
- 19132 udp (priority 3)
- 8192 tcp (priority 4)
- 25575 from 54.87.231.232 (priority 14)
- 25575 from 18.209.80.3 (priority 15)
- fragments from 54.87.231.232 (priority 16)
- fragments from 18.209.80.3 (priority 17)
- allow all icmp (priority 18)
- deny all ipv4 (priotiy 19)
