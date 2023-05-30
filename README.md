# ansible-collection-windows_sql_server
This collection contains example roles for setting up Windows SQL Server Stand Alone or AlwaysOn cluster.

This collection is meant for demo purposes only to set up a simple SQL Server AlwaysOn cluster, you would want to adopt
and extend it using other SQLServerDsc resources for your specific use case and any required Ansible Windows modules.

It includes the following roles:

  - ad_availability_group
  - alwayson
  - alwayson_common
  - install
  - sql_users

## Requirements

- oatakan.windows_cluster (collection)

## Usage

Install this collection locally:

    ansible-galaxy collection install oatakan.windows_sql_server -p ./collections

Then you can use the roles from the collection in your playbooks.

For SQL Server Stand Alone:

    ---
    - hosts: all
      vars:
        sql_server_local_users: true # use local users
      roles:
        - oatakan.windows_sql_server.sql_users # create users
        - oatakan.windows_sql_server.install


For SQL Server AlwaysOn cluster:

    ---
    - hosts: all
      roles:
        - oatakan.windows_cluster.join_domain
        - oatakan.windows_cluster.failover_common
        - oatakan.windows_sql_server.sql_users # optional for using domain users for SQL server
        - oatakan.windows_sql_server.install
        - oatakan.windows_sql_server.alwayson_common

    - hosts: primary_server
      roles:
        - role: oatakan.windows_cluster.failover
          first_node: true
      post_tasks:
        # this will set the ip address and hostname of the first node so that it's acccessible from the subsequent plays.
        - name: set cluster_first node
          add_host:
            name: cluster_first
            ip_address:  "{{ ansible_ip_addresses[0] | default(ansible_host) | default(ansible_ssh_host) }}"
            ansible_hostname: "{{ ansible_hostname | default(ansible_host) | default(ansible_ssh_host) }}"

    - hosts: secondary_server
      roles:
        - role: oatakan.windows_cluster.failover
          first_node: false

    # after fully functional Windows cluster, we move onto setting up alwayson cluster
    - hosts: primary_server
      roles:
        - oatakan.windows_sql_server.ad_availability_group # this needs to be set up once per AD
        - role: oatakan.windows_sql_server.alwayson
          first_node: true

    - hosts: secondary_server
      roles:
        - role: oatakan.windows_sql_server.alwayson
          first_node: false