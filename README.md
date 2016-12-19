# A collection of Ansible playbooks

## Introduction

This repository contains playbooks for various services. They are destined
to be used on cloud, but they should run correctly on any platform.

*Currently supported OS*: CentOS

## List of services / tasks

 - os_vm: Creating VMs on an OpenStack platform for the hosts
 - added_dns: Adding all hostnames in /etc/hosts of all hosts
 - base: Installing NTP, disabling security among others
 - epel: Declaring EPEL repository in YUM repo list
 - kerberos_kdc: Installing Kerberos KDC
 - kerberos_client: Installing Kerberos client
 - mariadb: Installing mariadb
 - cdh_base: Basic host configuration for Cloudera
 - cdh_scm_manager: Installing Cloudera Manager server
 - cdh_scm_agent: Installing Cloudera Manager Agent

More roles will be added in the future.

