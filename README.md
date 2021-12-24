# Linux Host

A collection of configuration files needed to build a new Linux host for the server.

Note: This should eventually become an Ansible playbook that automates the creation of a new Linux host. For now, this will do just to document all the configs needed.

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
