# Add databases and users to MySQL database

## Introduction

This role add databases and users to MySQL database. This role can be called
multiple times, each with different entries for MySQL.

This role requires that MySQL server is installed locally.

## Variables:

  - mysql_items: (list of dict) List of entries to add to MySQL. Each entry is
                 a dictionary with keys ("host", "user", "password").

Example:

mysql_items:
    - { host: "%", database: db1,  user: user1,  password: password1  }
    - { host: "localhost", database: db1,  user: user1,  password: password1  }
    - { host: "%", database: db2,  user: user2,  password: password2  }
    - { host: "locahost", database: db2,  user: user2,  password: password2  }

