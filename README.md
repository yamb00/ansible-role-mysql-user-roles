## Role Name

This ansible role allow the concept of roles for MySQL. Each users can be assigned to one or more defined roles.

#### Requirements

A MySQL Server must be installed and a user with grant privileges

#### Platforms

Currently it's been developed for, and tested on Ubuntu. It is assumed to work on other Debian distributions as well.

#### Role Variables

##### Default Variables

- 'mysql_login_user: root' - mysql user
- 'mysql_login_host: localhost' - mysql user host
- 'mysql_login_pass: ""' - mysql user password

###### User & Roles

```yml
mysql_user:
  - name: foo
    host: localhost
    password: ''
    roles:
      - webmaster
      - reader

mysql_user_roles:
  - name: webmaster
    priv: 
      - 'webdata.*:CREATE,SELECT'
      - 'stats.*:CREATE,SELECT'
  - name: reader
    priv: 
      - 'bigdata.*:SELECT'
```

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: localhost
      vars:
      	mysql_user:
		  - name: foo
		    host: localhost
		    password: ''
		    roles:
		      - webmaster
		mysql_user_roles:
		  - name: webmaster
		    priv: 
		      - 'webdata.*:CREATE,SELECT'
      roles:
         - { role: yamb00.mysql-user-roles }

License
-------

BSD