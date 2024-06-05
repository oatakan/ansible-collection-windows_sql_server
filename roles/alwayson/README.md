Role Name
=========

alwayson

Description
=========

This role creates SQL server AlwaysOn cluster.


Requirements
------------

- AD Controller
- Domain admin credentials
- Windows cluster is created, you can use oatakan.windows_cluster collection
- SQL Server AD users are created, you can use oatakan.windows_sql_server.sql_users
- SQL Server availability group objects are created in AD, you can use oatakan.windows_sql_server.ad_availability_group
- SQL Server is installed
- oatakan.windows_sql_server.alwayson_common role already run on both primary and secondary nodes

Role Variables
--------------

- alwayson_first_node: false
- alwayson_sql_server_availability_group_name: 'SQLAGN'
- alwayson_sql_server_availability_group_ip_address: '192.168.100.11/255.255.255.0'
- alwayson_sql_server_instance_name:  'MSSQLSERVER'

Dependencies
------------



Example Playbook
----------------
```yaml
---
- name: set up alwayson (primary)
  hosts: primary_server
  roles:
    - oatakan.windows_sql_server.ad_availability_group # this needs to be set up once per AD
    - role: alwayson
      alwayson_first_node: true

- name: set up alwayson (secondary)
  hosts: secondary_server
  roles:
    - role: alwayson
      alwayson_first_node: false
```
License
-------

MIT

Author Information
------------------

- [Orcun Atakan](https://github.com/oatakan/)