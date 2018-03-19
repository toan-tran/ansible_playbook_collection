# Delete databases and users from MySQL database


## Introduction

This role delete databases and users from MySQL database. This role can be called multiple times, each with different entries for MySQL.

This role requires that MySQL server is installed locally.


## Variables:

  - vault_mysql_root_password: (str) password for MySQL root user. Should be encrypted with Ansible vault.
  - mysql_items: (list of dict) List of entries to add to MySQL. Each entry is a dictionary with keys "user".

  The `mysql_populate` role also has a variable named `mysql_items`, which is used by `mysql_populate` to create databases and users. This variable can be used by this role to remove the same databases and users.


## Notes

  - This role must be called on MySQL server.
  - This role remove all users from MySQL, not just access from certain hosts. This means that it will remove all entries of this user from `mysql.user` table.


## Example:

For instances, in `mysql.user`:

| host                | user     | password                                  |
|---------------------|----------|-------------------------------------------|
| localhost           | user1    | *15221DE9A04689C4D312DEAC3B87DDF542AF439E |
| %                   | user1    | *15221DE9A04689C4D312DEAC3B87DDF542AF439E |
| test-0              | user1    | *15221DE9A04689C4D312DEAC3B87DDF542AF439E |
| localhost           | user2    | *2B03FE0359FAD3B80620490CE614F8622E0828CD |
| %                   | user2    | *2B03FE0359FAD3B80620490CE614F8622E0828CD |
| test-0              | user2    | *2B03FE0359FAD3B80620490CE614F8622E0828CD |

With `mysql_items`:

    - { host: "localhost", database: db1,  user: user1,  password: password1  }
    - { user: user2}

This role will remove all six entries of user1 and user2 from `mysql.user`, eventhough mysql_items tends to suggest that access host is 'localhost' for user1.
