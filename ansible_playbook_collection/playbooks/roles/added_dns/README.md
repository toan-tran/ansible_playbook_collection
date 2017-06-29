# Add DNS records to /etc/hosts

## Introduction

This role will add DNS record of all inventory hosts into /etc/hosts of every
host. This is useful if there is no DNS server for these hosts.

Work with CentOS / RHEL / Fedora / Debian / Ubuntu

*NOTE:* If there is DNS server which is capable of updating hosts dynamically,
it is strongly recommended to use this feature to keep the coherent with other
hosts that are not in the inventory. This role is used only if there is no
such a feature.

## Variables

  - domain_name: (string) if added, will add this as domain name of the DNS
                 records (<hostname>.<domain_name>)
  - kerberos_domain: (string) if no domain_name is defined, will use
                     kerberos_domain if declared as DNS domain name
                     (<hostname>.<kerberos_domain>)
If either of the above two variables is defined, the DNS records will only
contains short name.
  - additional_hosts: (list of string) additional DNS records to add into
                      /etc/hosts. Each line of the list is a DNS record.
                      E.g.
                        - 172.16.0.101  host-1.example1.com  host-1
                        - 172.16.1.102  host-2.example2.com  host-2

