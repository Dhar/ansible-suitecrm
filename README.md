SuiteCRM
======

Installs [SuiteCRM](http://suitecrm.com/) MAX edition using Nginx.

Requirements
------------

This role was created on/for Ubuntu Trusty installations and was specifically tested in an OpenVZ container environment.

You must download the SuiteCRM-7.1.2-MAX.zip file from the SuiteCRM site and place it in files/ before using this role.  SuiteCRM requires registration and login to download files.

Role Variables
--------------

The role uses the following variables, set in the defaults/main.yml file:

* `suitecrm_version` - Specific version of SuiteCRM to install (defaults to 7.1.2)
* `suitecrm_install_dir` - Directory to install SuiteCRM (defaults to /var/www)
* `suitecrm_frontend_host` - Hostname of SuiteCRM install (defaults to localhost)
* `suitecrm_database_host` - Hostname of MySQL database (defaults to localhost)
* `suitecrm_database_user` - SuiteCRM database username (defaults to suitecrm_admin)
* `suitecrm_database_password` - SuiteCRM database user password (defaults to ise982nxk)
* `suitecrm_timezone` - SuiteCRM server timezone (defaults to America/Los_Angeles)

Dependencies
------------

None

Usage
-----

    ansible-galaxy install garnold.suitecrm

Also check the [Ansible Galaxy](https://galaxy.ansibleworks.com/intro) about page.

Example Playbook
-------------------------

Example playbook for installing SuiteCRM database and web servers on separate systems:

    ---
    - hosts: crm-db
      roles:
      - { role: Ansibles.mysql, mysql_users: [{name: "{{ suitecrm_database_user }}", pass: "{{ suitecrm_database_password }}", host: "{{ suitecrm_frontend_host }}", priv: "*.*:ALL"}]}

    - hosts: crm-fe
      roles:
      - { role: ansible-suitecrm }

License
-------

MIT

Author Information
------------------

Gary Arnold

[GitHub project page](https://github.com/Dhar/ansible-suitecrm)
