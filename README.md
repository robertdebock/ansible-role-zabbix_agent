# [zabbix_agent](#zabbix_agent)

Install and configure zabbix_agent on your system.

|Travis|GitHub|GitLab|Quality|Downloads|Version|
|------|------|------|-------|---------|-------|
|[![travis](https://travis-ci.com/robertdebock/ansible-role-zabbix_agent.svg?branch=master)](https://travis-ci.com/robertdebock/ansible-role-zabbix_agent)|[![github](https://github.com/robertdebock/ansible-role-zabbix_agent/workflows/Ansible%20Molecule/badge.svg)](https://github.com/robertdebock/ansible-role-zabbix_agent/actions)|[![gitlab](https://gitlab.com/robertdebock/ansible-role-zabbix_agent/badges/master/pipeline.svg)](https://gitlab.com/robertdebock/ansible-role-zabbix_agent)|[![quality](https://img.shields.io/ansible/quality/35761)](https://galaxy.ansible.com/robertdebock/zabbix_agent)|[![downloads](https://img.shields.io/ansible/role/d/35761)](https://galaxy.ansible.com/robertdebock/zabbix_agent)|[![Version](https://img.shields.io/github/release/robertdebock/ansible-role-zabbix_agent.svg)](https://github.com/robertdebock/ansible-role-zabbix_agent/releases/)|

## [Example Playbook](#example-playbook)

This example is taken from `molecule/resources/converge.yml` and is tested on each push, pull request and release.
```yaml
---
- name: Converge
  hosts: all
  become: yes
  gather_facts: yes

  roles:
    - role: robertdebock.zabbix_agent
```

The machine needs to be prepared in CI this is done using `molecule/resources/prepare.yml`:
```yaml
---
- name: Prepare
  hosts: all
  gather_facts: no
  become: yes

  roles:
    - role: robertdebock.bootstrap
    - role: robertdebock.zabbix_repository
```

Also see a [full explanation and example](https://robertdebock.nl/how-to-use-these-roles.html) on how to use these roles.

## [Role Variables](#role-variables)

These variables are set in `defaults/main.yml`:
```yaml
---
# Values used to configure zabbix_agent.

zabbix_agent_server_address: 127.0.0.1
zabbix_agent_listen_port: 10050
zabbix_agent_server_active_address: 127.0.0.1
# Not mandatory, but possible to overwrite.
# zabbix_agent_source_ip: 127.0.0.1

zabbix_agent_hostname: "{{ ansible_fqdn }}"
zabbix_agent_hostmetadata: system.uname
zabbix_agent_timeout: 3

# Enable logging of remote commands by setting this value to 1.
zabbix_agent_logremotecommands: "1"
```

## [Requirements](#requirements)

- pip packages listed in [requirements.txt](https://github.com/robertdebock/ansible-role-zabbix_agent/blob/master/requirements.txt).

## [Status of requirements](#status-of-requirements)

The following roles are used to prepare a system. You may choose to prepare your system in another way, I have tested these roles as well.

| Requirement | Travis | GitHub |
|-------------|--------|--------|
| [robertdebock.bootstrap](https://galaxy.ansible.com/robertdebock/bootstrap) | [![Build Status Travis](https://travis-ci.com/robertdebock/ansible-role-bootstrap.svg?branch=master)](https://travis-ci.com/robertdebock/ansible-role-bootstrap) | [![Build Status GitHub](https://github.com/robertdebock/ansible-role-bootstrap/workflows/Ansible%20Molecule/badge.svg)](https://github.com/robertdebock/ansible-role-bootstrap/actions) |
| [robertdebock.zabbix_repository](https://galaxy.ansible.com/robertdebock/zabbix_repository) | [![Build Status Travis](https://travis-ci.com/robertdebock/ansible-role-zabbix_repository.svg?branch=master)](https://travis-ci.com/robertdebock/ansible-role-zabbix_repository) | [![Build Status GitHub](https://github.com/robertdebock/ansible-role-zabbix_repository/workflows/Ansible%20Molecule/badge.svg)](https://github.com/robertdebock/ansible-role-zabbix_repository/actions) |

## [Context](#context)

This role is a part of many compatible roles. Have a look at [the documentation of these roles](https://robertdebock.nl/) for further information.

Here is an overview of related roles:
![dependencies](https://raw.githubusercontent.com/robertdebock/drawings/artifacts/zabbix_agent.png "Dependency")

## [Compatibility](#compatibility)

This role has been tested on these [container images](https://hub.docker.com/u/robertdebock):

|container|tags|
|---------|----|
|el|7, 8|
|debian|buster|
|opensuse|all|
|ubuntu|focal, bionic|

The minimum version of Ansible required is 2.9, tests have been done to:

- The previous version.
- The current version.
- The development version.

## [Exceptions](#exceptions)

Some variarations of the build matrix do not work. These are the variations and reasons why the build won't work:

| variation                 | reason                 |
|---------------------------|------------------------|
| Alpine | Zabbix has [limited OS support](https://www.zabbix.com/download). |
| amazonlinux | Zabbix has [limited OS support](https://www.zabbix.com/download). |
| Archlinux | Zabbix has [limited OS support](https://www.zabbix.com/download). |
| CentOS 8 | Zabbix has [limited OS support](https://www.zabbix.com/download). |
| Debian | Zabbix has [limited OS support](https://www.zabbix.com/download). |
| Fedora | Zabbix has [limited OS support](https://www.zabbix.com/download). |
| openSUSE | Zabbix has [limited OS support](https://www.zabbix.com/download). |
| Ubuntu rolling | Zabbix has [limited OS support](https://www.zabbix.com/download). |


## [Testing](#testing)

[Unit tests](https://travis-ci.com/robertdebock/ansible-role-zabbix_agent) are done on every commit, pull request, release and periodically.

If you find issues, please register them in [GitHub](https://github.com/robertdebock/ansible-role-zabbix_agent/issues)

Testing is done using [Tox](https://tox.readthedocs.io/en/latest/) and [Molecule](https://github.com/ansible/molecule):

[Tox](https://tox.readthedocs.io/en/latest/) tests multiple ansible versions.
[Molecule](https://github.com/ansible/molecule) tests multiple distributions.

To test using the defaults (any installed ansible version, namespace: `robertdebock`, image: `fedora`, tag: `latest`):

```
molecule test

# Or select a specific image:
image=ubuntu molecule test
# Or select a specific image and a specific tag:
image="debian" tag="stable" tox
```

Or you can test multiple versions of Ansible, and select images:
Tox allows multiple versions of Ansible to be tested. To run the default (namespace: `robertdebock`, image: `fedora`, tag: `latest`) tests:

```
tox

# To run CentOS (namespace: `robertdebock`, tag: `latest`)
image="centos" tox
# Or customize more:
image="debian" tag="stable" tox
```

## [License](#license)

Apache-2.0


## [Author Information](#author-information)

[Robert de Bock](https://robertdebock.nl/)

Please consider [sponsoring me](https://github.com/sponsors/robertdebock).
