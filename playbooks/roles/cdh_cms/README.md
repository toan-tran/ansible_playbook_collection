# Install Cloudera Management Service - CMS #


## Introduction ##

This playbook will install Cloudera Managent Service (CMS) on CentOS or Ubuntu.

It requires that Cloudera Manager and Agents are properly set up. It will
install all CMS services in the first host of [cdh-cms] group using Cloudera API.

*IMPORTANT NOTE*:

Due to some reason Cloudera API does not accept API call for setting up services
if Cloudera Manager uses Express license. It would rise an Error:

  > "The feature Operational Reports is not available."

Only Trial or Enterprise license accepts these API calls. Thus Cloudera Manager
MUST activate one of these licenses before this to work.

The cloudera_scm_manager role activates Trial license by default.

## Variables ##

  - cloudera_admin_password: password for Cloudera Manager admin.
  - amondb: (dictionary) Database for Activity Monitoring Service

    >       {db_type: "database_type", db_host: "some_host", db_name: "some_database",  db_user: "some_user",  db_password: "some_password"}
    
    with database_type: mysql or postgre
  - rmandb: (dictionary) Database for Report Manager Service

    >        {db_type: "database_type", db_host: "some_host", db_name: "some_database",  db_user: "some_user",  db_password: "some_password"}

    with database_type: mysql or postgre

Without declared databases (amondb.db_host, rmandb.db_host), this role will try to use the first host in [mariadb] group
as the database, or if this later is missing, use the first host of [cdh-cms] as database.

## Other variables ##

  - fqdn: (optional) Fully Qualified Domain Name of the host. If set, will use host's fqdn value as
          fullname of the host in CMS template. Otherwise will use ansible_fqdn.

Note that by default Cloudera Agent reports back using Fully Qualified Domain Name (FQDN) from the same
Python code as Ansible ansible_fqdn:

>      python -c 'import socket; \
                  print socket.getfqdn(), socket.gethostbyname(socket.getfqdn())'

This may not be able to retrieve the correct FQDN in some cases.



## Notes on this playbook ##

  - This role MUST be launched on Cloudera Manger host
  - The host where CMS is installed MUST contains 'fqdn' variable which is the Fully Qualified
Domain Name of the host.
  - Due to some reason Cloudera API does not accept API call for setting up services if Cloudera
    Manager uses Express license. It would rise an Error:

    > "The feature Operational Reports is not available."




## Links ##

Manual instruction for installing Cloudera Manager:
  http://www.cloudera.com/documentation/enterprise/5-8-x/topics/installation_installation.html
  http://www.cloudera.com/documentation/enterprise/5-8-x/topics/cm_ig_install_path_b.html

A playbook for installing Cloudera cluster:
  https://github.com/cloudera/cloudera-playbook

