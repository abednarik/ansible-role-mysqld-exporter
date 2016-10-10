# Ansible Role: MySQL Exporter

An Ansible Role that installs [MySQL Exporter](https://github.com/prometheus/mysqld_exporter) on RedHat/CentOS or Debian/Ubuntu.

## Requirements

#### MySQL User with the following privileges

```sql
CREATE USER 'exporter'@'localhost' IDENTIFIED BY 'PASSWORD';
GRANT PROCESS, REPLICATION CLIENT,
SELECT ON *.* TO 'exporter'@'localhost' WITH MAX_USER_CONNECTIONS 3;
FLUSH PRIVILEGES;
```
*NOTE*: It is recommended to set a max connection limit for the user to avoid overloading the server with monitoring scrapes under heavy load.

# Role Variables



# Dependencies



# Example Playbook

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: username.rolename, x: 42 }

# License

[GPLv3](https://www.gnu.org/licenses/quick-guide-gplv3.html)

# Author Information

This role was created in 2016 by [Alejandro Bednarik](https://github.com/abednarik)
