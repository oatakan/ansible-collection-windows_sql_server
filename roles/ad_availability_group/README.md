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

- cluster_name: testcluster
- join_ou_path: '' # this is optional when joining to a specific ou path structure
- dns_domain_name: 'example.com'
- sql_server_availability_group_listener_name: 'SQLAGN'
- sql_server_availability_group_ip_address: '192.168.100.11/255.255.255.0'
- windows_ad_server_ip: '192.168.100.10'

Dependencies
------------



Example Playbook
----------------

    - hosts: servers
      roles:
         - ad_availability_group

License
-------

MIT

Author Information
------------------

- [Orcun Atakan](https://github.com/oatakan/)