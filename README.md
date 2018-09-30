splunk-common
=========

Installation and basic configuration of [Splunk Enterprise](https://www.splunk.com/en_us/download/splunk-enterprise.html).

Splunk Enterprise version updates can be installed by incrementing the `splunk_version` variable and its corresponding `splunk_build` variable.

LDAP authentication with Microsoft Active Directory can be configured with additional variables.

Requirements
------------

[pyOpenSSL](https://pypi.org/project/pyOpenSSL/) - To generate self-signed x509 certificate.

Role Variables
--------------

|Variable                    |Default                      |
|----------------------------|-----------------------------|
|`splunk_version`            |7.1.3                        |
|`splunk_build`              |51d9cac7b837                 |
|`splunk_common_enable_ssl`  |True                         |
|`splunk_common_http_port`   |8443                         |
|`splunk_common_admin_user`  |admin                        |
|`splunk_common_admin_passwd`|ThisShouldBeLong&Complex     |
|`splunk_common_admin_salt`  |c0be578b4b8d82fa             |
|`splunk_secret`             |SDWQAIOvoISFDrb2...          |
|`enable_ldap`               |False                        |
|`auth_settings_name`        |ActiveDirectory|
|`user_base_dn`              | |
|`group_base_dn`             | |
|`bind_dn`                   | |
|`bind_dn_password`          | |
|`ldap_host`                 | |
|`ldap_port`                 |389|
|`splunk_admin_ad_group`     | |
|`splunk_power_ad_group`     | |
|`splunk_user_ad_group`      | |

Please remember to set your own values for `splunk_common_admin_passwd`, `splunk_common_admin_salt` and [`splunk_secret`](https://docs.splunk.com/Documentation/Splunk/7.1.3/Security/Deploysecurepasswordsacrossmultipleservers
), ideally encrypting them with ansible-vault.


Dependencies
------------

None.

Example Playbook
----------------

Example playbook:

    - hosts: servers
      roles:
         - { role: andrewmackett.splunk_common, splunk_version: 7.1.3, splunk_build: 51d9cac7b837 }

There's also a Vagrantfile in [tests](./tests) that you can use to start up a local test server.

License
-------

MIT

Author Information
------------------

https://github.com/andrewmackett
