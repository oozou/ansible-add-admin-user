ansible-add-admin-user
========

Adds user account with sudo rights for all commands without password. This
account is usually the one used by the systems administrator or devops engineer
to login to a machine.

Requirements
------------

None.

Role Variables
--------------

* add_admin_user.admin.username
  * string
  * a user account will be created with this username
* add_admin_user.remove_all_other_sudo_rights
  * boolean (defaults to true)
* add_admin_user.use\_key\_url
  * boolean (defaults to false)
  * if true, then supply url with following var:
* add_admin_user.admin.key_url
  * string
  * url of the public key (https://github.com/user.keys)
* add_admin_user.use\_key\_file
  * boolean (defaults to false)
  * if true, then supply path with following var
* add_admin_user.admin.key_file
  * string
  * path to the key file (/home/user/.ssh/id_rsa.pub)

Example Playbook
-------------------------

```yaml
- hosts: webservers
  roles:
    - role: ansible-add-admin-user
      add_admin_user:
        # keep all other sudo lines in sudoers file
        remove_all_other_sudo_rights: false
        # use url for public key to add to authorized keys file
        use_key_url: true
        admin:
          username: snoopdogg
          key_url: https://github.com/snoopdogg.keys
```

Author
------

Rick Apichairuk

