zabbix_agent
=========

<img src="https://docs.ansible.com/ansible-tower/3.2.4/html_ja/installandreference/_static/images/logo_invert.png" width="10%" height="10%" alt="Ansible logo" align="right"/>
<a href="https://travis-ci.org/robertdebock/ansible-role-zabbix_agent"><img src="https://travis-ci.org/robertdebock/ansible-role-zabbix_agent.svg?branch=master" alt="Build status" align="left"/></a>

Install and configure zabbix_agent on your system.

<img src="https://img.shields.io/ansible/role/d/35761"/>
<img src="https://img.shields.io/ansible/quality/35761"/>

Example Playbook
----------------

This example is taken from `molecule/resources/playbook.yml`:
```yaml
---
- name: Converge
  hosts: all
  become: yes
  gather_facts: yes

  roles:
    - robertdebock.zabbix_agent
```

The machine you are running this on, may need to be prepared.
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

Role Variables
--------------

These variables are set in `defaults/main.yml`:
```yaml
---
# Values used to confiure zabbix_agent.
zabbix_agent_server_address: 127.0.0.1
zabbix_agent_listen_port: 10050
zabbix_agent_server_active_address: 127.0.0.1
zabbix_agent_source_ip: "{{ ansible_default_ipv4.address }}"

zabbix_agent_hostname: "{{ ansible_fqdn }}"
zabbix_agent_hostmetadata: system.uname
zabbix_agent_hostmetadataitem: system.uname
zabbix_agent_timeout: 3

# Enable remote commands by setting this value to 1.
zabbix_agent_enableremotecommands: 0

# Enable logging of remote commands by setting this value to 1.
zabbix_agent_logremotecommands: 1
```

Requirements
------------

- Access to a repository containing packages, likely on the internet.
- A recent version of Ansible. (Tests run on the current, previous and next release of Ansible.)

The following roles can be installed to ensure all requirements are met, using `ansible-galaxy install -r requirements.yml`:

```yaml
---
- robertdebock.bootstrap
- robertdebock.zabbix_repository

```

This role uses the following modules:
```yaml
---
- assert
- package
- service
- template
```

Context
-------

This role is a part of many compatible roles. Have a look at [the documentation of these roles](https://robertdebock.nl/) for further information.

Here is an overview of related roles:
![dependencies](https://raw.githubusercontent.com/robertdebock/drawings/artifacts/zabbix_agent.png "Dependency")


Compatibility
-------------

This role has been tested against the following distributions and Ansible version:

|distribution|ansible 2.7|ansible 2.8|ansible devel|
|------------|-----------|-----------|-------------|
|alpine-edge*|no|no|no*|
|alpine-latest|no|no|no*|
|archlinux|no|no|no*|
|centos-6|yes|yes|yes*|
|centos-latest|yes|yes|yes*|
|debian-stable|no|no|no*|
|debian-unstable*|no|no|no*|
|fedora-latest|no|no|no*|
|fedora-rawhide*|no|no|no*|
|opensuse-leap|no|no|no*|
|ubuntu-devel*|yes|yes|yes*|
|ubuntu-latest|yes|yes|yes*|
|ubuntu-rolling|no|no|no*|

A single star means the build may fail, it's marked as an experimental build.




Testing
-------

[Unit tests](https://travis-ci.org/robertdebock/ansible-role-zabbix_agent) are done on every commit and periodically.

If you find issues, please register them in [GitHub](https://github.com/robertdebock/ansible-role-zabbix_agent/issues)

To test this role locally please use [Molecule](https://github.com/ansible/molecule):
```
pip install molecule
molecule test
```

To test on Amazon EC2, configure [~/.aws/credentials](https://docs.aws.amazon.com/sdk-for-java/v1/developer-guide/credentials.html) and set a region using `export AWS_REGION=eu-central-1` before running `molecule test --scenario-name ec2`.

There are many specific scenarios available, please have a look in the `molecule/` directory.

License
-------

Apache-2.0


Author Information
------------------

[Robert de Bock](https://robertdebock.nl/)
