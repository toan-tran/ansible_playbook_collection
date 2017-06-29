# Base playbook for some useful feature

## Introduction

This role is optional. It adds some useful packages to work with the VMs.
This role will do the following:

  - Install and configure NTP
  - Configure Timezone
  - Install and configure Vim
  - Install and configure Screen
  - Disable SELinux and Firewall on RedHat family OS.

Work with RedHat family and Debian family OS.

## Variables

 - timezone: (string - file path) (default: Europe/Paris) Timezone to change to.
             The timezone files' root folder is /usr/share/zoneinfo/
