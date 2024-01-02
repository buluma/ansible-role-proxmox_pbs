# Ansible role [proxmox_pbs](https://galaxy.ansible.com/ui/standalone/roles/buluma/proxmox_pbs/documentation)

description

|GitHub|Version|Issues|Pull Requests|Downloads|
|------|-------|------|-------------|---------|
|[![github](https://github.com/buluma/ansible-role-proxmox_pbs/actions/workflows/molecule.yml/badge.svg)](https://github.com/buluma/ansible-role-proxmox_pbs/actions/workflows/molecule.yml)|[![Version](https://img.shields.io/github/release/buluma/ansible-role-proxmox_pbs.svg)](https://github.com/buluma/ansible-role-proxmox_pbs/releases/)|[![Issues](https://img.shields.io/github/issues/buluma/ansible-role-proxmox_pbs.svg)](https://github.com/buluma/ansible-role-proxmox_pbs/issues/)|[![PullRequests](https://img.shields.io/github/issues-pr-closed-raw/buluma/ansible-role-proxmox_pbs.svg)](https://github.com/buluma/ansible-role-proxmox_pbs/pulls/)|[![Ansible Role](https://img.shields.io/ansible/role/d/buluma/proxmox_pbs)](https://galaxy.ansible.com/ui/standalone/roles/buluma/proxmox_pbs/documentation)|

## [Example Playbook](#example-playbook)

This example is taken from [`molecule/default/converge.yml`](https://github.com/buluma/ansible-role-proxmox_pbs/blob/master/molecule/default/converge.yml) and is tested on each push, pull request and release.

```yaml
---
- name: Converge
  hosts: all
  become: true
  gather_facts: true
  # vars:
  #   example_var: "value"
  roles:
    - role: "buluma.proxmox_pbs"
```

The machine needs to be prepared. In CI this is done using [`molecule/default/prepare.yml`](https://github.com/buluma/ansible-role-proxmox_pbs/blob/master/molecule/default/prepare.yml):

```yaml
---
- name: Prepare
  hosts: all
  become: true
  gather_facts: true

  tasks:
    - name: Copy PVE Repository Template
      ansible.builtin.copy:
        content: |
            deb https://enterprise.proxmox.com/debian/pbs {{ ansible_distribution_release }} pbs-enterprise
        dest: /etc/apt/sources.list.d/pbs-enterprise.list
```

Also see a [full explanation and example](https://buluma.github.io/how-to-use-these-roles.html) on how to use these roles.

## [Role Variables](#role-variables)

The default values for the variables are set in [`defaults/main.yml`](https://github.com/buluma/ansible-role-proxmox_pbs/blob/master/defaults/main.yml):

```yaml
---
# Mostly tested and planned for Proxmox Backuper Server 2+/Debian 11 Bullseye
# Older versions may work

# https://pbs.proxmox.com/docs/installation.html#secureapt
proxmox_pve_repository_key: "https://enterprise.proxmox.com/debian/proxmox-release-bullseye.gpg"

# manages the Proxmox /etc/apt/sources.list
proxmox_pbs_enable_default_repository: true

# Disable Enterprise Repository
# https://pve.proxmox.com/wiki/Package_Repositories#sysadmin_enterprise_repo
proxmox_pbs_enable_enterprise_repository: false

# Enable the no subscription repository
# https://pve.proxmox.com/wiki/Package_Repositories#sysadmin_no_subscription_repo
# NOT recommended for production use
proxmox_pbs_enable_no_subscription_repository: true
```

## [Requirements](#requirements)

- pip packages listed in [requirements.txt](https://github.com/buluma/ansible-role-proxmox_pbs/blob/master/requirements.txt).


## [Context](#context)

This role is a part of many compatible roles. Have a look at [the documentation of these roles](https://buluma.github.io/) for further information.

Here is an overview of related roles:

![dependencies](https://raw.githubusercontent.com/buluma/ansible-role-proxmox_pbs/png/requirements.png "Dependencies")

## [Compatibility](#compatibility)

This role has been tested on these [container images](https://hub.docker.com/u/buluma):

|container|tags|
|---------|----|
|[EL](https://hub.docker.com/repository/docker/buluma/enterpriselinux/general)|all|
|[Amazon](https://hub.docker.com/repository/docker/buluma/amazonlinux/general)|Candidate|
|[Fedora](https://hub.docker.com/repository/docker/buluma/fedora/general)|all|
|[Ubuntu](https://hub.docker.com/repository/docker/buluma/ubuntu/general)|all|
|[Debian](https://hub.docker.com/repository/docker/buluma/debian/general)|all|

The minimum version of Ansible required is 2.12, tests have been done to:

- The previous version.
- The current version.
- The development version.

If you find issues, please register them in [GitHub](https://github.com/buluma/ansible-role-proxmox_pbs/issues)

## [Changelog](#changelog)

[Role History](https://github.com/buluma/ansible-role-proxmox_pbs/blob/master/CHANGELOG.md)

## [License](#license)

[MIT](https://github.com/buluma/ansible-role-proxmox_pbs/blob/master/LICENSE)

## [Author Information](#author-information)

[Shadow Walker](https://buluma.github.io/)

