# Hosts

A repo for people too lazy to set up Ansible.

This is a collection of config files for all of our hosts. These need to be manually kept up to date, for now.

Ideally, this contains enough info to recreate any of our hosts should we ever need to.

## Domains:
(GOOGLE) semivanilla.com:
Record |  Type  | Value
------ | :----: | ------
@      | A      | 69.129.212.212
www    | CNAME  | @
play   | A      | 69.129.212.210 
mc     | A      | 69.129.212.210 
store  | CNAME  | semivanilla.tebex.io.

(GOOGLE) newlandsmc.com:
Record |  Type  | Value
------ | :----: | ------
@      | A      | 69.129.212.212
www    | CNAME  | @
play   | A      | 69.129.212.211 
mc     | A      | 69.129.212.211 
store  | CNAME  | f85d22dd.webstore.tebex.io.

(GOOGLE) hardlinesmp.com:
Record |  Type  | Value
------ | :----: | ------
@      | A      | 69.129.212.212
www    | CNAME  | @
play   | CNAME  | @
mc     | CNAME  | @
store  | CNAME  | hardlinesmp.tebex.io.

(CLOUDFLARE) superminecraftservers.com:
Record |  Type  | Value
------ | :----: | ------
@      | A      | 69.129.212.212
www    | CNAME  | @
