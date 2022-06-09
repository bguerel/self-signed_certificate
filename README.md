![Header](https://raw.githubusercontent.com/bguerel/self-signed_certificate/main/self-signed_certificate.png "Header")

Generate a self-signed certificate with your own CA
========

[![Open Source Love](https://badges.frapsoft.com/os/v3/open-source.png?v=103)](https://opensource.org/licenses/OSL-3.0)
[![Author](https://img.shields.io/badge/Powered%20by-Benhur%20Gürel-blue)](https://github.com/bguerel/bguerel)
[![Ansible Galaxy Downloads](https://img.shields.io/ansible/role/d/52706?color=blue&label=Galaxy%20Downloads&logo=Ansible)](https://galaxy.ansible.com/bguerel/self_signed_certificate)
[![Version](https://img.shields.io/github/v/release/bguerel/self-signed_certificate?label=self-signed_certificate&logo=Ansible)](https://github.com/bguerel/self-signed_certificate/releases)

**Note:** Getting Chrome to accept self-signed localhost certificate.

## Description

:exclamation: Before using this role, you should know that all of my Ansible roles are tailored to my IT infrastructure. I therefore recommend that you analyze it carefully so that it can be safely installed on your servers.

## Requirements

- [x] Ansible >= 2.9

### Dependencies

- [x] PyOpenSSL >= 0.15 or cryptography >= 1.3

Installation
------------

- [x] git

Use `git@github.com:bguerel/self-signed_certificate.git` to pull the latest commit of the role from git.

Platforms
---------

```yaml
RedHat:
  versions:
    - all
Debian:
  versions:
    - all
Suse:
  versions:
    - all
```

Role Variables
--------------

The descriptions and default settings for all variables can be found in the **`defaults`** directory in the following file:

- **[defaults/main.yml](./defaults/main.yml)** default settings

## Example

### Configuration

```yaml
# Define a Domain Name for each node.
self_signed_domain:
  example-app-01v:
  - app01.example.local
  example-app-02v:
  - app02.example.local

# Directory of the certificate
self_signed_cert_path: "/etc/ssl/localcerts"

# The certificate issuer.
self_signed_organization_name: "BGUEREL Self-signed CA"

# Certificate Validity in days.
self_signed_expiration_date_in_days: 3650

# Generate diffie-hellman parameters with the default size (4096 bits).
self_signed_create_dhparam: yes

# Install the packages.
self_signed_install_pkgs: yes

# Python openssl dependencies.
self_signed_pkgs_name:
  - pyOpenSSL
```

### Playbook

Use it in a playbook as follows:

```yaml
- hosts: whatever
  become: yes
  roles:
    - self-signed_certificate
```

License
-------

[![MIT license](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)
