# SVMC-GAME-3

Dedicated server. Hosts the production servers.

NGINX is installed to serve the squaremap (port 8080). Accessed via reverse proxy through webserver. HTTPS is enabled via cert generated with OpenSSL:

`sudo openssl req -newkey rsa:2048 -x509 -sha256 -days 730 -nodes -out <ip.crt> -keyout <ip.key>`

Minecraft servers located at /var/minecraft/

mcrcon located at /var/minecraft/mcrcon

~~nbted located at /var/minecraft/nbted~~

Java is located at /usr/java/\<version\>

Backup drive is mounted with: https://linuxconfig.org/how-to-add-new-disk-to-existing-linux-system

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
- rsync
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
CREATE DATABASE asthonia_aurelium;
CREATE DATABASE asthonia_coreprotect;
CREATE DATABASE asthonia_gpdata;
CREATE DATABASE litebans;
CREATE DATABASE luckperms;
CREATE DATABASE premiumvanish;
CREATE DATABASE nickname;
CREATE DATABASE creative_plotsquared;
CREATE DATABASE creative_coreprotect;
CREATE DATABASE hardline_aurelium;
CREATE DATABASE hardline_luckperms;
CREATE DATABASE hardline_coreprotect;
CREATE DATABASE semivanilla_coreprotect;
CREATE DATABASE semivanilla_gpdata;
CREATE DATABASE semivanilla_luckperms;
CREATE DATABASE semivanilla_nickname;
CREATE DATABASE semivanilla_premiumvanish;
CREATE USER 'aurelium'@localhost IDENTIFIED BY 'NHCwp2D6NU9Z8cX5';
CREATE USER 'coreprotect'@localhost IDENTIFIED BY '3ZBwCESb6C65Rpda';
CREATE USER 'litebans'@localhost IDENTIFIED BY 'TA6gFmSbUqj8WexX';
CREATE USER 'luckperms'@localhost IDENTIFIED BY 'D744wXcSQr6hSwYQ';
CREATE USER 'griefprevention'@localhost IDENTIFIED BY 'NYBXJw9K9PhbeZkT';
CREATE USER 'plotsquared'@localhost IDENTIFIED BY 'Cy34cS4mWpdJ62X8';
CREATE USER 'premiumvanish'@localhost IDENTIFIED BY 'p9td448Rmn46jY36';
CREATE USER 'nickname'@localhost IDENTIFIED BY 'iE0vxIkXVlCe9Ue4';
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
GRANT ALL PRIVILEGES ON semivanilla_nickname.* TO 'nickname'@localhost;
GRANT ALL PRIVILEGES ON semivanilla_gpdata.* TO 'griefprevention'@localhost;
GRANT ALL PRIVILEGES ON semivanilla_coreprotect.* TO 'coreprotect'@localhost;
GRANT ALL PRIVILEGES ON semivanilla_luckperms.* TO 'luckperms'@localhost;
GRANT ALL PRIVILEGES ON semivanilla_premiumvanish.* TO 'premiumvanish'@localhost;
FLUSH PRIVILEGES;
```
