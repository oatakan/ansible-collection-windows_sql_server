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

- dns_domain_name: example.com
- mssql_username: sqladmin
- mssql_password: ''
- sql_server_instance_name:  'MSSQLSERVER'
- sql_server_svc_account_name: SASQLSvcAccount
- sql_server_agt_svc_account_name: SAAgtSvcAccount
- sql_server_local_users: false # set this to true to create local users instead of domain users

Dependencies
------------



Example Playbook
----------------

    - hosts: all
      roles:
        - alwayson_common

License
-------

MIT

Author Information
------------------

- [Orcun Atakan](https://github.com/oatakan/)