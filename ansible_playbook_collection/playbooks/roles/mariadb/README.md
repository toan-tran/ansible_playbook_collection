MariaDB Role

Using this Role
========

This role install engine mariadb if not present, create databases and users defined in Meta in others roles.
Add this role in your Meta main.yml to create your database and user.

Define your password user in vault file.
You can enter more than one user and databases.

Examples to create many databases and users:

````
dependencies:
  - { role: mariadb,mysql_items: [{database: "BDD", user: "USER1", password: "{{ vault_password_user1_myapp }}"}, {database: "BDD", user: "USER2", password: "{{ vault_password_user2_myapp }}"}]}
  - { role: mariadb,mysql_items: [{database: "BDD1", user: "USER", password: "{{ vault_password_user_myapp }}"}]}
  - { role: mariadb,mysql_items: [{database: "BDD1", user: "USER1", password: "{{ vault_password_user1_myapp }}"}]}
````
