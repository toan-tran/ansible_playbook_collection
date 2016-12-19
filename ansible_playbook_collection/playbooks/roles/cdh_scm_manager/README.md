# Install Cloudera Manager on CentOS #

## Introduction ##

This playbook will install Cloudera Manager 5.5.x on CentOS.

In conjunction with the Cloudera Manager Agent playbook, it forms a starting
point for creating / managing a Cloudera Hadoop cluster.

* IMPORTANT * This playbook is for Dev/Test platform.

There are two options on databases for Cloudera Manager:

 - Embedded Postgre from Cloudera Manager. This option is good for Dev/Test
   purpose but not recommanded for production.
 - Independent database (recommended: Postgre cluster). This option is
   recommended for production.

If 'cloudera_external_database' is not defined, this playbook will install and
use the embeded Postgre from Cloudera.

If 'cloudera_external_database' is defined, this playbook will use the external
database whose informations are defined within this variable.

cloudera_external_database:
   type: Database type (mysql / postgre / oracle)
   host: Database host name or IP
   root_user: name of privileged user, 'root' for MySQL, 'postgre' for Postgre, '' for Oracle
   root_password: password of the privileged user
   cloudera_db: name of the database used for Cloudera
   cloudera_user: user for Cloudera
   cloudera_pwd: passwod for Cloudera

## Notes on this playbook ##

 - Use OpenJDK 1.8.0 as default. To use another java package, declare as 'java_package'variable
 - If local_cloudera_manager_repo_url is defined, uses it as Cloudera Manager repository URL,
   if not, use official Cloudera Manager repository

## Links ##

Manual instruction for installing Cloudera Manager:
  http://www.cloudera.com/documentation/enterprise/5-5-x/topics/installation_installation.html
  http://www.cloudera.com/documentation/enterprise/5-5-x/topics/cm_ig_install_path_b.html

