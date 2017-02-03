# Ansible role for creating VMs with attached volumes on OpenStack for the inventory

## DESCRIPTION

This role will create the VMs for the inventory on OpenStack platform.

## REQUIREMENTS
    - Python's shade module
    - Openstack's credential is loaded in environment variables (e.g. source openrc.src)

## USAGE

This role should be executed in a machine with OpenStack's credential already loaded in environment variables, usually the localhost.

For using this role, each host defined in the inventory must have following variables (defined in host_vars or group_vars):

  - ansible_host: host IP address
  - ansible_private_key_file: path to VM's SSH private key file. Its filename must be as same as name of the SSH key registered on the cloud.
  - cloud_flavor_id: VM's Flavor ID
  - cloud_image_id: VM's Image ID
  - cloud_security_groups: (comma separated string) VM's security groups.
  - cloud_network_id: VM's Network name or ID

The following variables are optional.

  - cloud_volumes: (list of dict) If defined, will create volumes and attach to the VM
      - size: (imperative) size of volume in GB
      - device: (imperative) device to attach inside the VM
      - type: (optional) volume type. If not define, will use default type of the cloud

As current state, this role create VMs and volumes, it does not remove them, so scale down is not possible.

This role add following metadata to VMs (volumes do not support metadata in ansible yet) so that we can use to get dynamic inventory.

  - ansible:deployment_name: (string) deployment name, to be able to distinguish VMs of different playbooks on the same OpenStack
  - ansible:groups: (comma separated string) list of groups of the host
