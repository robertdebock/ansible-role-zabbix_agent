# [Ansible role zabbix_agent](#zabbix_agent)

Install and configure zabbix_agent on your system.

|GitHub|GitLab|Downloads|Version|
|------|------|---------|-------|
|[![github](https://github.com/robertdebock/ansible-role-zabbix_agent/workflows/Ansible%20Molecule/badge.svg)](https://github.com/robertdebock/ansible-role-zabbix_agent/actions)|[![gitlab](https://gitlab.com/robertdebock-iac/ansible-role-zabbix_agent/badges/master/pipeline.svg)](https://gitlab.com/robertdebock-iac/ansible-role-zabbix_agent)|[![downloads](https://img.shields.io/ansible/role/d/robertdebock/zabbix_agent)](https://galaxy.ansible.com/robertdebock/zabbix_agent)|[![Version](https://img.shields.io/github/release/robertdebock/ansible-role-zabbix_agent.svg)](https://github.com/robertdebock/ansible-role-zabbix_agent/releases/)|

## [Example Playbook](#example-playbook)

This example is taken from [`molecule/default/converge.yml`](https://github.com/robertdebock/ansible-role-zabbix_agent/blob/master/molecule/default/converge.yml) and is tested on each push, pull request and release.

```yaml
---
- name: Converge
  hosts: all
  become: true
  gather_facts: true

  roles:
    - role: robertdebock.zabbix_agent
```

The machine needs to be prepared. In CI this is done using [`molecule/default/prepare.yml`](https://github.com/robertdebock/ansible-role-zabbix_agent/blob/master/molecule/default/prepare.yml):

```yaml
---
- name: Prepare
  hosts: all
  become: true
  gather_facts: false

  roles:
    - role: robertdebock.bootstrap
    - role: robertdebock.ca_certificates
    - role: robertdebock.zabbix_repository
```

Also see a [full explanation and example](https://robertdebock.nl/how-to-use-these-roles.html) on how to use these roles.

## [Role Variables](#role-variables)

The default values for the variables are set in [`defaults/main.yml`](https://github.com/robertdebock/ansible-role-zabbix_agent/blob/master/defaults/main.yml):

```yaml
---
# Values used to configure zabbix_agent.

zabbix_agent_server_address: "127.0.0.1"
zabbix_agent_listen_port: 10050
zabbix_agent_server_active_address: "127.0.0.1"
# Not mandatory, but possible to overwrite.
# zabbix_agent_source_ip: "127.0.0.1"

zabbix_agent_hostname: "{{ ansible_fqdn }}"
zabbix_agent_hostmetadata: system.uname
zabbix_agent_timeout: 3

# Enable logging of remote commands by setting this value to 1.
zabbix_agent_logremotecommands: "1"
```

## [Requirements](#requirements)

- pip packages listed in [requirements.txt](https://github.com/robertdebock/ansible-role-zabbix_agent/blob/master/requirements.txt).

## [State of used roles](#state-of-used-roles)

The following roles are used to prepare a system. You can prepare your system in another way.

| Requirement | GitHub | GitLab |
|-------------|--------|--------|
|[robertdebock.bootstrap](https://galaxy.ansible.com/robertdebock/bootstrap)|[![Build Status GitHub](https://github.com/robertdebock/ansible-role-bootstrap/workflows/Ansible%20Molecule/badge.svg)](https://github.com/robertdebock/ansible-role-bootstrap/actions)|[![Build Status GitLab](https://gitlab.com/robertdebock-iac/ansible-role-bootstrap/badges/master/pipeline.svg)](https://gitlab.com/robertdebock-iac/ansible-role-bootstrap)|
|[robertdebock.ca_certificates](https://galaxy.ansible.com/robertdebock/ca_certificates)|[![Build Status GitHub](https://github.com/robertdebock/ansible-role-ca_certificates/workflows/Ansible%20Molecule/badge.svg)](https://github.com/robertdebock/ansible-role-ca_certificates/actions)|[![Build Status GitLab](https://gitlab.com/robertdebock-iac/ansible-role-ca_certificates/badges/master/pipeline.svg)](https://gitlab.com/robertdebock-iac/ansible-role-ca_certificates)|
|[robertdebock.zabbix_repository](https://galaxy.ansible.com/robertdebock/zabbix_repository)|[![Build Status GitHub](https://github.com/robertdebock/ansible-role-zabbix_repository/workflows/Ansible%20Molecule/badge.svg)](https://github.com/robertdebock/ansible-role-zabbix_repository/actions)|[![Build Status GitLab](https://gitlab.com/robertdebock-iac/ansible-role-zabbix_repository/badges/master/pipeline.svg)](https://gitlab.com/robertdebock-iac/ansible-role-zabbix_repository)|

## [Context](#context)

This role is a part of many compatible roles. Have a look at [the documentation of these roles](https://robertdebock.nl/) for further information.

Here is an overview of related roles:
![dependencies](https://raw.githubusercontent.com/robertdebock/ansible-role-zabbix_agent/png/requirements.png "Dependencies")

## [Compatibility](#compatibility)

This role has been tested on these [container images](https://hub.docker.com/u/robertdebock):

|container|tags|
|---------|----|
|[EL](https://hub.docker.com/r/robertdebock/enterpriselinux)|9|
|[Debian](https://hub.docker.com/r/robertdebock/debian)|bullseye|
|[Ubuntu](https://hub.docker.com/r/robertdebock/ubuntu)|focal|

The minimum version of Ansible required is 2.12, tests have been done to:

- The previous version.
- The current version.
- The development version.

If you find issues, please register them in [GitHub](https://github.com/robertdebock/ansible-role-zabbix_agent/issues).

## [License](#license)

[Apache-2.0](https://github.com/robertdebock/ansible-role-zabbix_agent/blob/master/LICENSE).

## [Author Information](#author-information)

[robertdebock](https://robertdebock.nl/)

Please consider [sponsoring me](https://github.com/sponsors/robertdebock).
