Shibboleth Service Provider (SP)
=========

This role installs the Shibboleth Service Provider package maintained by SWITCH, the Swiss NREN. 

Requirements
------------

This role does not install the webserver that will be protected by the SP. It is recommended to use a current version of Apache for this. An Ansible Playbook that sets up the complete stack can be found on [Github:](https://github.com/ubuntunet/eduID_ServiceProvider "Shibboleth Service Provider")

Role Variables
--------------

There is a file vars/main.yml.example that can be copied and used as template to define the variables

```
cp vars/main.yml.example vars/main.example
```

### federation
Name of the Federation that this SP will be joining

### fqdn 
Fully Qualified Domain Name. Can be a domain name or IP address

### entity_id
Identity of the SP. Usually no need to change this.

### support_first_name, support_last_name, support_email
Contact details of support desk. It is recommend to not use a personal email address.

### admin_first_name, admin_last_name, admin_email
Contact details of technical admistrator

### admin_first_name, admin_last_name, admin_email
Contact details of organisational admistrator

### technical_first_name, technical_last_name, technical_email
Contact details of technician

### default_ds_url
URL of the federations central Discovery Service (cDS). This should only be used if it is not possible to show the user login directly within the application

### show_attribute_values
Show the actual values of the attributes of an authenticated user under https://{{ fqdn }}/Shibboleth.sso/Session

### metadata_url
URL where the SP can download the metadata of the federation

### metadata_file
Name of the locally stored metadata file



Dependencies
------------

Any playbook for Apache.

Example Playbook
----------------

- name: Install Shibboleth Service Provider
  hosts: servers
  become: True

  roles:
    - { role: chrohrer.shibboleth-sp }


License
-------

MIT

Author Information
------------------

Chris Rohrer works for UbuntuNet Alliance in Lilongwe/Malawi.