# Ansible Role: MySQL Exporter

[![Build Status](https://travis-ci.org/abednarik/ansible-role-mysqld-exporter.svg?branch=master)](https://travis-ci.org/abednarik/ansible-role-mysqld-exporter) 
[![CircleCI](https://circleci.com/gh/abednarik/ansible-role-mysqld-exporter.svg?style=shield)](https://circleci.com/gh/abednarik/ansible-role-mysqld-exporter)

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

## Role Variables

### Mandatory variables

User, password, host and port for mysql_exporter.

```yml
prometheus_mysqld_exporter_env: 'user:password@(hostname:port)/'
```

### Optional variables: general settings

User-configurable defaults:

```yaml
prometheus_user:   prometheus
prometheus_group:  prometheus

prometheus_mysqld_exporter_version: 0.9.0

gosu_version: '1.10'

prometheus_install_path:  /opt/prometheus
prometheus_log_path:      /var/log/prometheus
prometheus_pid_path:      /var/run/prometheus
```

## Dependencies

None.

## Example Playbook

```yml
- hosts: all
  become: True
  roles:
    - abednarik.mysqld-exporter

  vars:
    prometheus_mysqld_exporter_env: 'exporter:password@(localhost:3306)/'
```

## License

[GPLv3](https://www.gnu.org/licenses/quick-guide-gplv3.html)

## Author Information

This role was created in 2016 by [Alejandro Bednarik](https://github.com/abednarik)

## Note

Thus role is based on William-Yeh great work with ansible/prometheus. See
https://github.com/William-Yeh/ansible-prometheus for more information.
