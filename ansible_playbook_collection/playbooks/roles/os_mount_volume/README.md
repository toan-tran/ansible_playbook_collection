# Ansible role for mounting volumes inside hosts

## Introduction

This role will format and mount volumes inside hosts.

This role complements the os_vm role which creates VMs and attached volumes.
While os_vm creates resources, this role configures the attached resources.
Together these two roles prepare the infrastructure for other application
playbook to use.

Unlike os_vm, however, os_mount_volume is not dependent on the cloud
infrastructure. It can be used alone in any infrastructure.

Why separate the two roles? Because some application playbooks may configure
the volumes themselves. Thus it is better to separated the two roles.


## How to use this role

To use this role, admin must specify the volume description in cloud_volumes
variable (defined as host_vars or group_vars) as same as os_vm role:

  - cloud_volumes: (list of dict) If not defined, will ignore the host.
      - size: (used in os_vm role) size of volume in GB
      - type: (used in os_vm role) volume type
      - device: (imperative) device to attach inside the VM
      - format: (imperative) format of the volume
      - mount_folder: (imperative) folder to mount the volume to

## Behavior

 - If 'cloud_volumes' is not defined in the host, then no volume is required,
   simply ignore the host

 - If 'format' is not defined, then the volume is attached (by os_vm role) but
   will not be handled by this role. It is the case, for example, when the
   application playbook configures the volume itself.
