MariaDb
=========

A role that installs MariaDb, adds a single database with a single database user

Requirements
------------

None

Role Variables
--------------

- **mariadb_app_name**: The name of the application this database is supporting
  - Defaults to *exampleapp*
- **mariadb_root_password**: The root password for MySql. If it's blank, a random password is generated
  - Defaults to *Random 20 character password with letters, digits, and punctuation*
- **mariadb_dbuser_password**: The password for the specific database made for the application. If it's blank, a random password is generated
  - Defaults to *Random 20 character password with letters, digits, and punctuation*
- **mariadb_root_pw_file**: Where the root password should be stored. If blank, don't save the password locally.
  - Defaults to */etc/mysql/root_pw*
- **mariadb_dbuser_password_file**: Where the database user password should be stored. If blank, don't save the password locally.
  - Defaults to */etc/mysql/user_{{ mariadb_dbuser }}*

Note: **mariadb_dbname** and **mariadb_dbuser** are available for use in subsequent roles and plays

Dependencies
------------

No role dependencies.

Example Playbooks
----------------

```yaml
# Install the Database and make a myapp_db and myapp_dbuser, with random passwords saved in /etc/mysql
    - role: 'irontooch.maria_db'
      vars:
        mariadb_app_name: "myapp"
```

```yaml
# Install the Database and make a myapp_db and myapp_dbuser, with specific passwords saved in /etc/mysql
    - role: 'irontooch.maria_db'
      vars:
        mariadb_app_name: "myapp"
        mariadb_root_password: "my_root_pw1234"
        mariadb_dbuser_password: "my_user_pw1234"
```

```yaml
# Install the Database and make a myapp_db and myapp_dbuser, but do not save the passwords
    - role: 'irontooch.maria_db'
      vars:
        mariadb_app_name: "myapp"
        mariadb_root_pw_file: ""
        mariadb_dbuser_password_file: ""
```

License
-------

GPL v3.0

Author Information
------------------

Author is IronTooch
