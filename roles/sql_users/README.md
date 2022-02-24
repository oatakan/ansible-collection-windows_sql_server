Role Name
=========

sql_users

Description
=========

This role creates SQL server service users on AD Active Directory controller using domain admin credentials.


Requirements
------------

- AD Controller
- Domain admin credentials

Role Variables
--------------

- dns_domain_name: example.com
- sql_server_svc_account_name: SASQLSvcAccount
- sql_server_agt_svc_account_name: SAAgtSvcAccount
- sql_server_svc_accounts_password: ''
- sql_server_local_users: false # set this to true to create local users instead of domain users
- sql_server_users_group_name: SQL Users

Dependencies
------------



Example Playbook
----------------

    - hosts: servers
      roles:
         - sql_users

License
-------

MIT

Author Information
------------------

- [Orcun Atakan](https://github.com/oatakan/)