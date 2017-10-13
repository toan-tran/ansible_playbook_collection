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
   cloudera_user: user of Cloudera database
   cloudera_password: password of Cloudera database

cloudera_external_database should be stored in an encrypted vars file.


## Other variables ##

cloudera_admin_password: password for Cloudera Manager admin. Should be stored in an
                         encrypted vars file.
cloudera_manager_version: (optional) the version of Cloudera Manager to install. If not
                          present, will install latest version of the repository.
cloudera_manager_repository: (optional) Repository for Cloudera Manager. If use in conjunction
                             with cloudera_manager_version, make sure that the repository
                             contains the Cloudera Manager of the required version.
                             If not present, will use official Cloudera repository. 
cloudera_parcel_repositories: (optional) Customized Cloudera parcel repository.
                              If not set, use official Cloudera parcel repository.
cloudera_use_trial_license: (optional) true (default value) if activate Trial license,
                            false if continue using Express license.
                            IMPORTANT: to be able to set up services using Cloudera API,
                            we must activate Trial license. Otherwise API commands return
                            Error "The feature Operational Reports is not available."
                            It does not prevent us from setting up services using Wizard though.


## Notes on this playbook ##

 - Uses OpenJDK 1.8.0 as default for CentOS. To use another java package, declare as 'java_package'variable
   Debian family uses Oracle JDK 1.8.
 - Uses Oracle Java 1.8.0 for Ubuntu.
 - If cloudera_manager_version is defined and cloudera_manager_repository is not, the playbook will try to
   use official Cloudera repository, which is at https://archive.cloudera.com/cm{4,5}/. Make sure that the
   repository of the required version is available for the host OS.

## Links ##

Manual instruction for installing Cloudera Manager:
  http://www.cloudera.com/documentation/enterprise/5-8-x/topics/installation_installation.html
  http://www.cloudera.com/documentation/enterprise/5-8-x/topics/cm_ig_install_path_b.html

A playbook for installing Cloudera cluster:
  https://github.com/cloudera/cloudera-playbook

