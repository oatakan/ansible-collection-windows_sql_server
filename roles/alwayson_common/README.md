Role Name
=========

alwayson_common

Description
=========

This role implements prereq steps for SQL server AlwaysOn cluster.


Requirements
------------

- AD Controller
- Domain admin credentials
- Windows cluster is created, you can use oatakan.windows_cluster collection
- SQL Server AD users are created, you can use oatakan.windows_sql_server.sql_users
- SQL Server availability group objects are created in AD, you can use oatakan.windows_sql_server.ad_availability_group
- SQL Server is installed

Role Variables
--------------

- alwayson_common_dns_domain_name: example.com
- alwayson_common_mssql_username: sqladmin
- alwayson_common_mssql_password: ''
- alwayson_common_sql_server_instance_name:  'MSSQLSERVER'
- alwayson_common_alwayson_common_sql_server_svc_account_name: SASQLSvcAccount
- alwayson_common_alwayson_common_sql_server_agt_svc_account_name: SAAgtSvcAccount
- alwayson_common_sql_server_local_users: false # set this to true to create local users instead of domain users

Dependencies
------------



Example Playbook
----------------
```yaml
---
- name: alwayson common configuration
  hosts: all
  roles:
    - alwayson_common
```
License
-------

MIT

Author Information
------------------

- [Orcun Atakan](https://github.com/oatakan/)