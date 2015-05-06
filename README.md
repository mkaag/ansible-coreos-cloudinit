coreos-cloudinit
================

[![Ansible Galaxy](https://img.shields.io/badge/galaxy-mkaag.coreos--cloudinit-660198.svg)](https://galaxy.ansible.com/list#/roles/3629)

Ansible role for deploying cloud config (user_data) on CoreOS. This role has been inspired from [Tazjin's Blog](http://www.tazj.in/en/1410951452).
You can find more details about the cloud-config on https://coreos.com/docs/cluster-management/setup/cloudinit-cloud-config/.

Requirements
------------

Install [Ansible](http://www.ansible.com) on your computer, refer to the official [documentation](http://docs.ansible.com/intro_installation.html) for more details.

Installation
------------

`ansible-galaxy install mkaag.coreos-cloudinit`

Role Variables
--------------

- coreos_discovery: Cluster discovery URL, see the [doc for mor details](https://coreos.com/docs/cluster-management/setup/cluster-discovery/)
- coreos_channel: could either be `stable`, `beta` or `alpha`, see the [doc for more details](https://coreos.com/docs/cluster-management/setup/switching-channels/)
- coreos_reboot: could either be `best-effort`, `etcd-lock`, `reboot` or `off`, see the [doc for more details](https://coreos.com/docs/cluster-management/setup/update-strategies/)
- machine_metadata: see the [doc for more details](https://coreos.com/docs/launching-containers/launching/launching-containers-fleet/)
- username: see the [doc for more details](https://coreos.com/docs/cluster-management/setup/cloudinit-cloud-config/#users)
- userssh: certificate found in `~/.ssh/id_rsa.pub` (without the `ssh-rsa` starting block)

Dependencies
------------

None

Example Playbook
----------------

```yml
---
- hosts: coreos
  vars:
    coreos_discovery=https://discovery.etcd.io/12345678901234567890
    coreos_channel=stable
    coreos_reboot=etcd-lock
    machine_metadata=[region=ams3,public_ip=$public_ipv4]
    username: core
    userssh: AAAAB3N...
  roles:
    - mkaag.coreos-cloudinit
```

License
-------

MIT