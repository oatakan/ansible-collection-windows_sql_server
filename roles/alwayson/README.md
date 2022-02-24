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

- first_node: false
- sql_server_availability_group_name: 'SQLAGN'
- sql_server_availability_group_ip_address: '192.168.100.11/255.255.255.0'
- sql_server_instance_name:  'MSSQLSERVER'

Dependencies
------------



Example Playbook
----------------

    - hosts: primary_server
      roles:
        - oatakan.windows_sql_server.ad_availability_group # this needs to be set up once per AD
        - role: alwayson
          first_node: true

    - hosts: secondary_server
      roles:
        - role: alwayson
          first_node: false

License
-------

MIT

Author Information
------------------

- [Orcun Atakan](https://github.com/oatakan/)