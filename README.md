# Hosts

A repo for people too lazy to set up Ansible.

This is a collection of config files for all of our hosts. These need to be manually kept up to date, for now.

Ideally, this contains enough info to recreate any of our hosts should we ever need to.

## Domains:
semivanilla.com:
Record |  Type  | Value
------ | :----: | ------
@      | A      | 135.148.121.47
www    | CNAME  | @
play   | A      | 135.148.137.94
mc     | CNAME  | play.semivanilla.com
store  | CNAME  | f85d22dd.webstore.tebex.io.

asthonia.com:
Record |  Type  | Value
------ | :----: | ------
@      | A      | 135.148.121.47
www    | CNAME  | @
play   | A      | 135.148.137.94
mc     | CNMA   | play.asthonia.com
store  | 301    | store.semivanilla.com

khavalon.com:
Record |  Type  | Value
------ | :----: | ------
@      | A      | 135.148.121.47
www    | CNAME  | @
play   | A      | 135.148.137.94
mc     | CNMA   | play.khavalon.com
store  | 301    | store.semivanilla.com