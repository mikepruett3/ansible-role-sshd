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

Additional (**Optional**) variable is **sshd_config**. This is used to restrict what groups of users can SSH into the server, via the **AllowGroups** configuration in the sshd_config file. This group can be either local or some other external group (like *LDAP/AD*). If this variable is not defined, then the default SSH config will allow any valid user to login via SSH.

``` yaml
sshd_config: mygroup
```

Role variables can be stored with the hosts.yaml file, or in the main variables file.

Dependencies
------------

None.

Example Playbook
----------------

``` yaml
    - hosts: servers
      roles:
         - role: mikepruett3.sshd
```

Tags
----

The **groups** tag has been configured to allow for playbook reused when adding multiple groups to the SSH **AllowGroups** configuration.

``` yaml
    - hosts: servers
      roles:

         - role: mikepruett3.sshd
           vars:
             sshd_config: my1stgroup

         - role: mikepruett3.sshd
           tags:
             groups
           vars:
             sshd_config: my2ndgroup
```

License
-------

MIT

Author Information
------------------

Role created by [mikepruett3](https://github.com/mikepruett3) on [Github.com](https://github.com/mikepruett3/ansible-role-sshd)
