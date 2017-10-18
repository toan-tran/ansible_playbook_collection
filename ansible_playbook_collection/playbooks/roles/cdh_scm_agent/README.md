# Install Cloudera Manager Agent on CentOS #

## Introduction ##

This playbook will install Cloudera Manager Agent 5.x.x on RHEL and Debian family OS.

In conjunction with the CDH_SCM_Manager playbook, it forms a starting
point for creating / managing a Cloudera Hadoop cluster.

## Variables ##

cloudera_manager_repository: (optional) Customized repository for Cloudera Manager,
                             If not set, use official Cloudera Manager repository

cloudera_java_family: (optional) Java family (7/8) to install. Default value: 8

## Other variables ##

  - fqdn: (optional) Fully Qualified Domain Name of the host. If set, will use host's fqdn value as
          fullname of the host in CMS template. Otherwise will use ansible_fqdn.

Note that by default Cloudera Agent reports back using Fully Qualified Domain Name (FQDN) from the same
Python code as Ansible ansible_fqdn:

>      python -c 'import socket; \
                  print socket.getfqdn(), socket.gethostbyname(socket.getfqdn())'

This may not be able to retrieve the correct FQDN in some cases.


## Notes on this playbook ##

 - This role tries to install Oracle Java, but will fall back to OpenJDK if failed

## Links ##

Manual instruction for installing Cloudera Manager Agent:
 - http://www.cloudera.com/documentation/enterprise/5-5-x/topics/installation_installation.html
 - http://www.cloudera.com/documentation/enterprise/5-5-x/topics/cm_ig_install_path_b.html

