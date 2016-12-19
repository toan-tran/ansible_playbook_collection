# Install Cloudera Manager Agent on CentOS #

## Introduction ##

This playbook will install Cloudera Manager Agent 5.5.x on CentOS.

In conjunction with the Cloudera Manager playbook, it forms a starting
point for creating / managing a Cloudera Hadoop cluster.

**IMPORTANT** : This playbook is for Dev/Test platform.

There are two options on databases for Cloudera Manager:

 - Embedded Postgre from Cloudera Manager. This option is good for Dev/Test
   purpose but not recommanded for production.
 - Independent database (recommended: Postgre cluster). This option is
   recommended for production.

This playbook will just use embedded Postgre from Cloudera Manager for Dev/Test
purpose. For production, use another playbook (in conjunction with a Postgre
playbook).


## Notes on this playbook ##

 - Use OpenJDK 1.8.0
 - Use embedded Postgre for Cloudera Manager

## Links ##

Manual instruction for installing Cloudera Manager Agent:
 - http://www.cloudera.com/documentation/enterprise/5-5-x/topics/installation_installation.html
 - http://www.cloudera.com/documentation/enterprise/5-5-x/topics/cm_ig_install_path_b.html

