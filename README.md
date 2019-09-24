vagrant_user
============

Role that helps to create and configure Vagrant user on a VirtualBox VM.

The configuration of the role is done in such way that it should not be necessary
to change the role for any kind of configuration. All can be done either by
changing role parameters or by declaring completely new configuration as a
variable. That makes this role absolutely universal. See the examples below for
more details.

Please report any issues or send PR.


Example
-------

```yaml
---

# Example of basic usage
- hosts: myhost
  roles:
    - vagrant_user
```


Role variables
--------------

List of variables used by the role:

```yaml
# Vagrant user name
vagrant_user_name: vagrant

# Vagrant user UID
vagrant_user_uid: 17935

# Vagrant password
vagrant_user_password: "{{ 'vagrant' | password_hash('sha512', 'vagsalt') }}"

# Vagrant group
vagrant_user_group: users

# Sudo settings
vagrant_user_sudo: |
    Defaults !requiretty
    vagrant ALL=(ALL) NOPASSWD: ALL

# Vagrant insecure key
# (https://github.com/mitchellh/vagrant/blob/master/keys/vagrant.pub)
vagrant_user_public_key: ssh-rsa AAAAB3NzaC1yc2EAAAABIwAAAQEA6NF8iallvQVp22WDkTkyrtvp9eWW6A8YVr+kz4TjGYe7gHzIw+niNltGEFHzD8+v1I2YJ6oXevct1YeS0o9HZyN1Q9qgCgzUFtdOKLv6IedplqoPkcmF0aYet2PkEDo3MlTBckFXPITAMzF8dJSIFo9D8HfdOV0IAdx4O7PtixWKn5y2hMNG0zQPyUecp4pzC6kivAIhyfHilFR61RGL+GPXQ2MWZWFYbAGjyiYJnAmCP3NOTd0jMZEnDkbUvxhMmBYSdETk1rRgm+R4LOzFUGaHqHDLKLX+FIPKcF96hrucXzcWyLbIbEgE98OHlnVYCzRdK8jlqm8tehUc9c9WhQ== vagrant insecure public key
```


Dependencies
------------

- [vbox_additions](https://github.com/jtyr/ansible-vbox_additions) (optional)


License
-------

MIT


Author
------

Jiri Tyr
