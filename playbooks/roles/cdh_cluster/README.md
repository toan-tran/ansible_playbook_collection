# Install Cloudera Hadoop Cluster #


## Introduction ##

This playbook will install Cloudera Hadoop Cluster (CMS) on CentOS or Ubuntu.

It requires that Cloudera Manager and Agents are properly set up.

The cluster is composed of following roles, each corresponds to an inventory
group:

  - 1 Cloudera Manager  (inventory group: [cdh-managers] )
  - 1 Cloudera Master 1 (inventory group: [cdh-master1] )
  - 1 Cloudera Master 2 (inventory group: [cdh-master2] )
  - n Cloudera Worker   (inventory group: [cdh-workers] )

See [cloudera_cluster.hosts](../../../example_inventories/cloudera_cluster.hosts) for inventory example,
which set up Cloudera Cluster on 7 hosts (which also include Cloudera Manger and Management Service from other roles).

The following services are installed with the cluster:

  - HDFS
  - Hive
  - Pig
  - Oozie
  - Spark
  - YARN
  - Zookeeper
  - HUE


*IMPORTANT NOTE*:

  1. Due to some reason Cloudera API does not accept API call for setting up services
    if Cloudera Manager uses Express license. It would rise an Error:

    > "The feature Operational Reports is not available."

    Only Trial or Enterprise license accepts these API calls. Thus Cloudera Manager
    MUST activate one of these licenses before this to work.

    The cloudera_scm_manager role activates Trial license by default.

  2. If there is already a Hadoop cluster with the same name on Cloudera cluster, it will simply consider that the cluster is already deployed and does not yield an error. That said, this role will neither fix an erred cluster, nor modify an existing cluster.


## Variables ##

  - cloudera_manager_version: version of Cloudera Manager. Must be the same as in cloudera_scm_manager role
  - cloudera_admin_password: password for Cloudera Manager admin.
  - cloudera_version: (default "5.8.5") Cloudera version to install. Cannot newer than Cloudera Manager.
  - cloudera_product: (default "5.8.5-1.cdh5.8.5.p0.5") Cloudera product. Must be correspondent to cloudera_version and host OS.
                      User can consult the list of available products at: http://archive.cloudera.com/cdh5/parcels/
                      For instance, CDH 5.8.5 on CentOS7 : http://archive.cloudera.com/cdh5/parcels/5.8.5/ shows

    >     CDH-5.8.5-1.cdh5.8.5.p0.5-el7.parcel

    In this case cloudera_product=5.8.5-1.cdh5.8.5.p0.5
  - cloudera_clustername: (optional) Name of the cluster. Default is 'cluster1'.
  - hivedb: (dictionary) Database for Hive

    >       {db_type: "database_type", db_host: "some_host", db_name: "some_database",  db_user: "some_user",  db_password: "some_password"}
    
    with database_type: mysql or postgre
  - huedb: (dictionary) Database for HUE

    >        {db_type: "database_type", db_host: "some_host", db_name: "some_database",  db_user: "some_user",  db_password: "some_password"}

    with database_type: mysql or postgre

  - ooziedb: (dictionary) Database for Oozie

    >        {db_type: "database_type", db_host: "some_host", db_name: "some_database",  db_user: "some_user",  db_password: "some_password"}

    with database_type: mysql or postgre

These above databases must be properly set up.


## Other variables ##

  - fqdn: (optional) Fully Qualified Domain Name of the host. If set, will use host's fqdn value as
          fullname of the host in CMS template. Otherwise will use ansible_fqdn.

Note that by default Cloudera Agent reports back using Fully Qualified Domain Name (FQDN) from the same
Python code as Ansible ansible_fqdn:

```
python -c 'import socket; print socket.getfqdn(), socket.gethostbyname(socket.getfqdn())'
```

This may not be able to retrieve the correct FQDN in some cases.


## Notes on this playbook ##

  - This role MUST be launched on Cloudera Manger host (inventory group: [cdh-managers])
  - Due to some reason Cloudera API does not accept API call for setting up services if Cloudera
    Manager uses Express license. It would rise an Error:

    > "The feature Operational Reports is not available."


## Links ##

Manual instruction for installing Cloudera Cluster:

  http://www.cloudera.com/documentation/enterprise/5-8-x/topics/installation_installation.html
  http://www.cloudera.com/documentation/enterprise/5-8-x/topics/cm_ig_install_path_b.html

A playbook for installing Cloudera cluster:

  https://github.com/cloudera/cloudera-playbook

