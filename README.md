# Hosts

A repo for people too lazy to set up Ansible.

This is a collection of config files for all of our hosts. These need to be manually kept up to date, for now.

Ideally, this contains enough info to recreate any of our hosts should we ever need to.

## Domains:
semivanilla.com:
Record |  Type  | Value
------ | :----: | ------
@      |   A    | 135.148.121.47
www    | CNAME  | @
play   | CNAME  | 51.222.244.67
mc     | CNAME  | play.semivanilla.com
store  | CNAME  | 41cb4817.webstore.tebex.io.

asthonia.com:
Record |  Type  | Value
------ | :----: | ------
@      |   A    | 135.148.121.47
www    | CNAME  | @
store  | CNAME  | 83bca8bf.webstore.tebex.io.


semi-vanilla.com, semi-vanilla.net, semivanilla.org, semivanill.co:
Record |  Type  | Value
------ | :----: | ------
\*      |   CNAME    | semivanilla.com

asthonia.net, asthonia.org, asthonia.co:
Record |  Type  | Value
------ | :----: | ------
\*      |   CNAME    | asthonia.com
