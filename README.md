Ansible Role: SSHD
=========

Ansible role to configure SSH daemon on Linux Servers.

Requirements
------------

The role does not require anyting to run on RHEL and its derivatives.

Role Variables
--------------

Available variables are listed below, along with default values (see ```defaults/main.yml```):

``` yaml
password_authentication: "no"
public_key_authentication: "yes"
permit_root_login: "no"

ssh_port: 22
use_dns: "no"
ignore_rhosts: "yes"

permit_empty_password: "no"
challenge_response_auth: "no"

gss_api_authentication: "no"
x11_forwarding: "no"

client_alive_int: "3600"
client_alive_max: "3"

login_grace_time: "1m"
max_auth_tries: "4"

log_level: "VERBOSE"

banner_console: "/etc/issue"
banner_remote: "/etc/issue.net"
```

Role variables can be stored with the hosts.yaml file, or in the main variables file.

Dependencies
------------

None.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

``` yaml
    - hosts: servers
      roles:
         - role: mikepruett3.sshd
```

License
-------

MIT

Author Information
------------------

Role created by [mikepruett3](https://github.com/mikepruett3/ansible-role-sshd) on [Github.com](https://github.com/mikepruett3/ansible-role-sshd)
