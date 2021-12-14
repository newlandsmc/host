# Linux Host

A collection of configuration files needed to build a new Linux host for the server.

Note: This should eventually become an Ansible playbook that automates the creation of a new Linux host. For now, this will do just to document all the configs needed.

## Packages Installed:

- OpenJDK from https://adoptium.net/
- Git
- tar

## Users created:

- minecraft /var/minecraft /bin/bash minecraft
- \<all admins\>


## Firewall:

- 25565 tcp/udp
- 80,443 tcp
- 22 tcp
