Role Name
=========

install

Description
=========

This role installs SQL server.


Requirements
------------

- When using AD users for Stand Alone installation, SQL Server AD users are created, you can use 
oatakan.windows_sql_server.sql_users

Role Variables
--------------

- install_dns_domain_name: example.com  # when using domain users
- install_mssql_username: sqladmin
- install_mssql_password: ''
- install_sql_server_instance_name:  'MSSQLSERVER'
- install_sql_server_features:
    - SQLENGINE
    - FullText
    - Replication
- install_sql_server_svc_account_name: SASQLSvcAccount
- install_sql_server_agt_svc_account_name: SAAgtSvcAccount
- install_sql_server_svc_accounts_password: ''
- install_sql_server_local_users: false # set this to true to create local users instead of domain users
- install_iso_path: '{{ ansible_env.TEMP }}\sql2019.iso'
- install_iso_url: '\\file_server\sql2019.iso' # this can be a network share or http url

Dependencies
------------



Example Playbook
----------------
```yaml
---
- name: install sql server
  hosts: all
  roles:
    - install
```
License
-------

MIT

Author Information
------------------

- [Orcun Atakan](https://github.com/oatakan/)