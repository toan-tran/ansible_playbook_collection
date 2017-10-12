# Install Cloudera Manager #


## Introduction ##

This playbook will install Cloudera Manager 5.x on CentOS or Ubuntu.

In conjunction with the Cloudera Manager Agent playbook, it forms a starting
point for creating / managing a Cloudera Hadoop cluster.

There are two options on databases for Cloudera Manager:

 - Embedded Postgre from Cloudera Manager. This option is good for Dev/Test
   purpose but not recommanded for production.
 - Independent database (e.g. MariaDB). This option is
   recommended for production.

If 'cloudera_external_database' is not defined, this playbook will install and
use the embeded Postgre from Cloudera.

If 'cloudera_external_database' is defined, this playbook will use the external
database whose informations are defined within this variable.

cloudera_external_database:
   type: Database type (mysql / postgre / oracle)
   host: Database host name or IP
   cloudera_db: name of the database used for Cloudera
   cloudera_user: user for Cloudera
   cloudera_pwd: passwod for Cloudera

cloudera_external_database should be stored in an encrypted vars file.


## Other variables ##

cloudera_admin_password: password for Cloudera Manager admin. Should be stored in an
                         encrypted vars file.
cloudera_manager_repository: (optional) Customized repository for Cloudera Manager,
                             If not set, use official Cloudera Manager repository
cloudera_parcel_repositories: (optional) Customized Cloudera parcel repository.
                              If not set, use official Cloudera parcel repository.
cloudera_version: (optional) customized Cloudera version. If not set, use default
                  (which is the latest) version.


## Notes on this playbook ##

 - Uses OpenJDK 1.8.0 as default for CentOS. To use another java package, declare as 'java_package'variable
   Debian family uses Oracle JDK 1.8.
 - Uses Oracle Java 1.8.0 for Ubuntu.


## Links ##

Manual instruction for installing Cloudera Manager:
  http://www.cloudera.com/documentation/enterprise/5-8-x/topics/installation_installation.html
  http://www.cloudera.com/documentation/enterprise/5-8-x/topics/cm_ig_install_path_b.html

A playbook for installing Cloudera cluster:
  https://github.com/cloudera/cloudera-playbook

