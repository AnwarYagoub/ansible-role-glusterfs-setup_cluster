Ansible Role: GlusterFS
=========

Set up a GlusterFS cluster on Linux servers.

Requirements
------------

TO BE ADDED

Role Variables
--------------

| Variable                        | usage                                                              |
| ------------------------------- | ------------------------------------------------------------------ |
| `gluster_servers`               | List of servers FQDNs to setup GlusterFS on                        |
| `create_replicated_test_volume` | Whether to create a replicated GlusterFS volume for testing or not |

Dependencies
------------

  - AnwarYagoub.glusterfs (Role)
  - gluster.gluster (Collection)

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      gather_facts: false
      strategy: linear
      vars:
        gluster_servers:
          - node-1.glusterfs.lab
          - node-2.glusterfs.lab
          - node-3.glusterfs.lab
      tasks:

        - name: Setup
          ansible.builtin.setup:
            gather_subset:
              - '!all'
              - '!min'
              - 'distribution'

        - name: Include anwaryagoub.glusterfs role
          ansible.builtin.include_role:
            name: anwaryagoub.glusterfs_setup_cluster

License
-------

MIT / BSD

Author Information
------------------

This role was created in 2024 by [Anwar Yagoub](https://github.com/AnwarYagoub)
