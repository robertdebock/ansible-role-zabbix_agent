zabbix_agent
=========

[![Build Status](https://travis-ci.org/robertdebock/ansible-role-zabbix_agent.svg?branch=master)](https://travis-ci.org/robertdebock/ansible-role-zabbix_agent)

Install and configure zabbix_agent on your system.

Example Playbook
----------------

This example is taken from `molecule/default/playbook.yml`:
```yaml
---
- name: Converge
  hosts: all
  gather_facts: false
  become: true

  roles:
    - role: robertdebock.bootstrap
    - role: robertdebock.zabbix_repository
    - role: robertdebock.zabbix_agent

```

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

# Some Docker containers do not allow managing services, rebooting and writing
# to some locations in /etc. The role skips tasks that will typically fail in
# Docker. With this parameter you can tell the role to -not- skip these tasks.
zabbix_agent_ignore_docker: yes

# To update all packages installed by this roles, set `zabbix_agent_package_state` to `latest`.
zabbix_agent_package_state: present

```

Requirements
------------

- Access to a repository containing packages, likely on the internet.
- A recent version of Ansible. (Tests run on the last 3 release of Ansible.)

The following roles can be installed to ensure all requirements are met, using `ansible-galaxy install -r requirements.yml`:

```yaml
---
- robertdebock.bootstrap
- robertdebock.zabbix_repository

```

Context
-------

This role is a part of many compatible roles. Have a look at [the documentation of these roles](https://robertdebock.nl/) for further information.

Here is an overview of related roles:
![dependencies](https://raw.githubusercontent.com/robertdebock/drawings/artifacts/zabbix_agent.png "Dependency")


Compatibility
-------------

This role has been tested against the following distributions and Ansible version:

|distribution|ansible 2.6|ansible 2.7|ansible devel|
|------------|-----------|-----------|-------------|
|alpine-edge*|no|no|no*|
|alpine-latest|no|no|no*|
|archlinux|no|no|no*|
|centos-6|yes|yes|yes*|
|centos-latest|yes|yes|yes*|
|debian-latest|yes|yes|yes*|
|debian-stable|yes|yes|yes*|
|debian-unstable*|yes|yes|yes*|
|fedora-latest|no|no|no*|
|fedora-rawhide*|no|no|no*|
|opensuse-leap|no|no|no*|
|opensuse-tumbleweed|no|no|no*|
|ubuntu-artful|no|no|no*|
|ubuntu-devel*|yes|yes|yes*|
|ubuntu-latest|yes|yes|yes*|

A single star means the build may fail, it's marked as an experimental build.

Testing
-------

[Unit tests](https://travis-ci.org/robertdebock/ansible-role-zabbix_agent) are done on every commit and periodically.

If you find issues, please register them in [GitHub](https://github.com/robertdebock/ansible-role-zabbix_agent/issues)

To test this role locally please use [Molecule](https://github.com/metacloud/molecule):
```
pip install molecule
molecule test
```

To test on Amazon EC2, configure [~/.aws/credentials](https://docs.aws.amazon.com/sdk-for-java/v1/developer-guide/credentials.html) and `export AWS_REGION=eu-central-1` before running `molecule test --scenario-name ec2`.

There are many specific scenarios available, please have a look in the `molecule/` directory.

Run the [ansible-galaxy](https://github.com/ansible/galaxy-lint-rules) and [my](https://github.com/robertdebock/ansible-lint-rules) lint rules if you want your change to be merges:

```shell
git clone https://github.com/ansible/ansible-lint.git /tmp/ansible-lint
ansible-lint -r /tmp/ansible-lint/lib/ansiblelint/rules .

git clone https://github.com/robertdebock/ansible-lint /tmp/my-ansible-lint
ansible-lint -r /tmp/my-ansible-lint/rules .
```

License
-------

Apache-2.0


Author Information
------------------

[Robert de Bock](https://robertdebock.nl/) <robert@meinit.nl>
