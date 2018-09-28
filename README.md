Solr Uninstall
=========
[![License](https://img.shields.io/badge/license-Apache-green.svg?style=flat)](https://raw.githubusercontent.com/lean-delivery/ansible-role-solr-uninstall/master/LICENSE)
[![Build Status](https://travis-ci.org/lean-delivery/ansible-role-solr-uninstall.svg?branch=master)](https://travis-ci.org/lean-delivery/ansible-role-solr-uninstall)
## Summary

This role:
  - Uninstalls Solr on Centos 7, Ubuntu or Windows host

Requirements
------------
  - Minimal Version of the ansible for installation: 2.5
  - **Solr installed** [![Build Status](https://travis-ci.org/lean-delivery/ansible-role-solr-standalone.svg?branch=master)](https://travis-ci.org/lean-delivery/ansible-role-solr-standalone)
  - **Supported OS**:
    - CentOS
      - 7
    - Ubuntu
    - Windows
      - "Windows Server 2008"
      - "Windows Server 2008 R2"
      - "Windows Server 2012"
      - "Windows Server 2012 R2"
      - "Windows Server 2016"
      - "Windows 7"
      - "Windows 8.1"
      - "Windows 10"

[Prepared Windows System](https://docs.ansible.com/ansible/latest/user_guide/windows_setup.html)

## Role Variables
  - `solr_version` - matches available version on https://archive.apache.org/dist/lucene/solr/. Tested versions 5.3-7.1.x
    default: `7.1.0`
  - `overrride_dest_main_path` - root directory to store solr folder
    default: `/opt`
    default: `C:\Solr`
  - `overrride_dest_solr_path` - solr folder path
    default: `{{ dest_main_path }}/solr-{{ solr_version }}`
    default: `{{ dest_main_path }}\\solr-{{ solr_version }}`
  - `solr_user` - os user to run solr service
    default: `solr`
  - `solr_group` - os group for user
    default: `solr`
  - `solr_service_name` - solr service name
    default: `solr`
  - `solr_base_path` - path to solr base
    default: `/var/solr`
  - `solr_insh_default` - path to solr.in.sh
    default: `/etc/default/solr.in.sh`
  - `solr_with_systemd` - to run solr as a service
    default: `True`
  - `solr_remove_user` - to remove user and group
    default: `False`

Example Inventory
----------------
[solr]
solr.example.com

[solrwin]
solrwin.example.com

[solrwin:vars]
ansible_user=admin
ansible_password=password
ansible_connection=winrm
ansible_winrm_server_cert_validation=ignore

Example Playbook
----------------

```yml
- name: Uninstall Solr
  hosts: solr
  roles:
    - role: lean-delivery.solr_uninstall
```

License
-------

Apache

Author Information
------------------

authors:
  - Lean Delivery Team <team@lean-delivery.com>