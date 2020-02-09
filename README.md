Role Name
=========

vvmware: Vvmware

[![Build Status](https://travis-ci.org/cmihai-ansible/vvmware.svg?branch=master)](https://travis-ci.org/cmihai-ansible/vvmware)

Ansible galaxy:
---------------

[https://galaxy.ansible.com/devops-toolbox.vvmware](https://galaxy.ansible.com/devops-toolbox.vvmware)

```bash
ansible-galaxy install devops-toolbox.vvmware
```

Requirements
------------

- For RHEL, a Red Hat subscription or functional local repository.
- Ansible 2.4 or higher

Role Variables
--------------

```yaml
vvmware_packages_state: present
vvmware_remove_packages: true
vvmware_enable_service: true
vvmware_enable_selinux: true
vvmware_copy_templates: true
vvmware_firewall_configure: true
vvmware_firewall_rules:
  - service: ssh
  - port: 3389
vvmware_users:
  - user: devops
    group: docker
vvmware_selinux_booleans:
  - name: ftp_home_dir
    state: true
    persistent: true
```

Dependencies
------------

- For Red Hat, subscription-manager.

Example Playbook
----------------

```yaml
---
- name: Install vvmware on localhost
  hosts:
    - localhost
  connection: local

  tasks:
    - name: vvmware is configured
      import_role:
        name: devops-toolbox.vvmware
      vars:
        vvmware_packages_state: present
        vvmware_remove_packages: true
        vvmware_enable_service: true
        vvmware_enable_selinux: true
        vvmware_copy_templates: true
        vvmware_firewall_configure: true
        vvmware_firewall_rules:
          - service: ssh
          - port: 3389
        vvmware_users:
          - user: devops
            group: docker
        vvmware_selinux_booleans:
          - name: ftp_home_dir
            state: true
            persistent: true
      tags: vvmware
```

License
-------

MIT

Author Information
------------------

- [Mihai Criveti](https://www.linkedin.com/in/devops-toolbox.)
