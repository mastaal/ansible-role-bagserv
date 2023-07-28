ansible-role-bagserv
====================

[![CI badge](https://github.com/mastaal/ansible-role-bagserv/workflows/CI/badge.svg?event=push)](https://github.com/mastaal/ansible-role-bagserv/actions/workflows/ci.yml)

Ansible role for deploying the bagserv utility from [bagconv](https://github.com/berthubert/bagconv).
bagserv, developed by Bert Hubert, provides a simple way to interact with the BAG, the official Dutch Building and Addresses database.

Requirements
------------

This role is written and tested for Ubuntu (version 22.04 LTS).

**You will need a good internet connection and enough available space to run this role!**
The fully uncompressed BAG XML dump is about 83GB in size; the compressed zip
as provided by the Kadaster is about 3GB in size. The generated sqlite3 database is about 11GB uncompressed, and about 3.5GB when using ZFS with zstd compression. So in order to run this role, be sure your target has enough available space. I recommend using a filesystem that allows for transparent compression, such as ZFS or btrfs.

Role Variables
--------------

```
bagserv_repo_url: "https://github.com/berthubert/bagconv.git"
```
URL to the respective bagconv repo. Change this if you want to install a fork.

```
bagserv_install_path: "/opt/bag/bagconv"
```
Path where bagconv is installed. This includes source coude, binaries, downloaded XML (zip) files and generated sqlite3 database.

```
bagserv_force_clone: true
```
Whether or not to discard local modifications (force clone).

```
bagserv_version: "HEAD"
```
Which version of the repository to checkout.

Dependencies
------------

No other roles are required.

Example Playbook
----------------

```
    - hosts: bagserv-host
      roles:
         - role: mastaal.bagserv
```

License and author information
------------------------------

Copyright (c) 2023 Martijn Staal

This role is licensed under the EUPL (European Union Public License), version 1.2 (Commission Implementing Decision (EU) 2017/863), or, at your option, any later version. The English and Dutch texts of this license are provided in LICENSE and LICENSE.NL respectively.
