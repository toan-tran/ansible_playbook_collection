# A collection of Ansible playbooks

## Introduction

This repository contains playbooks for various services. They are destined
to be used on cloud, but they should run correctly on any platform.

*Currently supported OS*: CentOS / Ubuntu (some roles)

## List of services / tasks

 - added_dns: Adding all hostnames in /etc/hosts of all hosts
 - base: Install NTP, disabling security among others
 - cdh_base: Basic host configuration for Cloudera
 - cdh_cms: Install Cloudera Management System (CMS) on Cloudera Manager
 - cdh_scm_agent: Install Cloudera Manager Agent
 - cdh_scm_manager: Install Cloudera Manager server
 - epel: Declaring EPEL repository in YUM repo list
 - kerberos_client: Install Kerberos client
 - kerberos_kdc: Install Kerberos KDC
 - mariadb: Install mariadb
 - mysql_populate: Create databases and users with access rights in MyQSL/MariaDB
 - openvpn: Install OpenVPN server
 - os_mount_volume: Mounting volumes inside VMs for Ansible inventory
 - os_vm: Creating VMs and attached volumes on an OpenStack platform for Ansible inventory
 - python27: Install Python version 2.7
 - python3: Install Python 3
 - wait_host: Wait for host to start

More roles will be added in the future.

