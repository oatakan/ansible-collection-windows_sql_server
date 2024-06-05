Role Name
=========

ad_availability_group

Description
=========

This role creates cluster objects on the Active Directory controller using domain admin credentials.


Requirements
------------

- AD Controller
- Domain admin credentials

Role Variables
--------------

- ad_availability_group_cluster_name: testcluster
- ad_availability_group_join_ou_path: '' # this is optional when joining to a specific ou path structure
- ad_availability_group_dns_domain_name: 'example.com'
- ad_availability_group_sql_server_availability_group_listener_name: 'SQLAGN'
- ad_availability_group_sql_server_availability_group_ip_address: '192.168.100.11/255.255.255.0'
- ad_availability_group_windows_ad_server_ip: '192.168.100.10'

Dependencies
------------



Example Playbook
----------------

```yaml
---
- name: setup availability group
  hosts: servers
  roles:
     - ad_availability_group
```

License
-------

MIT

Author Information
------------------

- [Orcun Atakan](https://github.com/oatakan/)