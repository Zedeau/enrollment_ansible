# enrollment_ansible
Ansible role to enroll RHEL hosts to the Satellite/Capsule server


Example of a playbook.yml


```
- hosts: all
  vars:
    adm_group: 
    gid_adm_group: 
    rex_user: 
    home_dir: 
    folder:
# Repos to activate on the hosts
#repos: "rhel-7-server-satellite-tools-6.7-rpms,rhel-server-rhscl-7-rpms,rhel-7-server-rh-common-rpms,rhel-7-server-rpms,rhel-7-server-extras-rpms"
    repos: "*"
    download_method: http
    bootstrap_path: /tmp/bootstrap.py
  vars_files:
# Using ansible-vault
    - satellite_credentials.yml
  roles:
    - enrollment_ansible
```


Example of the hosts file

```
[Europe]
testhost.local

[Europe:vars]
region=Europe
foreman_fqdn=satellite.local
organization="Startx"
location="Europe/Paris"
activationkey="AK_RHEL7"
hostgroup="HG_RHEL7"
```


Do not forget to create a satellite_credentials.yml using ansible-vault so you can store the Satellite 6 admin credentials
