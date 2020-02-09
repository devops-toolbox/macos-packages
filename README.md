Role Name
=========

macos-packages: Macos-packages

[![Build Status](https://travis-ci.org/cmihai-ansible/macos-packages.svg?branch=master)](https://travis-ci.org/cmihai-ansible/macos-packages)

Ansible galaxy:
---------------

[https://galaxy.ansible.com/devopstoolbox.macos-packages](https://galaxy.ansible.com/devopstoolbox.macos-packages)

```bash
ansible-galaxy install devopstoolbox.macos-packages
```

Requirements
------------

- For RHEL, a Red Hat subscription or functional local repository.
- Ansible 2.4 or higher

Role Variables
--------------

```yaml
macos-packages_packages_state: present
macos-packages_remove_packages: true
macos-packages_enable_service: true
macos-packages_enable_selinux: true
macos-packages_copy_templates: true
macos-packages_firewall_configure: true
macos-packages_firewall_rules:
  - service: ssh
  - port: 3389
macos-packages_users:
  - user: devops
    group: docker
macos-packages_selinux_booleans:
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
- name: Install macos-packages on localhost
  hosts:
    - localhost
  connection: local

  tasks:
    - name: macos-packages is configured
      import_role:
        name: devopstoolbox.macos-packages
      vars:
        macos-packages_packages_state: present
        macos-packages_remove_packages: true
        macos-packages_enable_service: true
        macos-packages_enable_selinux: true
        macos-packages_copy_templates: true
        macos-packages_firewall_configure: true
        macos-packages_firewall_rules:
          - service: ssh
          - port: 3389
        macos-packages_users:
          - user: devops
            group: docker
        macos-packages_selinux_booleans:
          - name: ftp_home_dir
            state: true
            persistent: true
      tags: macos-packages
```

License
-------

MIT

Author Information
------------------

- [Mihai Criveti](https://www.linkedin.com/in/crivetimihai)
