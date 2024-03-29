# enrollment_ansible
Ansible role to enroll RHEL hosts to the Satellite/Capsule server


Example of a playbook.yml


```
- hosts: all
  vars:
    rex_user: remote_user
    home_dir: "home/dir"
# Repos to activate on the hosts
#repos: "rhel-7-server-satellite-tools-6.7-rpms,rhel-server-rhscl-7-rpms,rhel-7-server-rh-common-rpms,rhel-7-server-rpms,rhel-7-server-extras-rpms"
    repos: "*"
    download_method: http
    bootstrap_path: /tmp/bootstrap.py
    sudoers: /etc/sudoers/nopasswd
  vars_files:
# Using ansible-vault
    - satellite_credentials.yml
  roles:
    - enrollment_ansible
```


Example of the hosts file

```
[all:vars]
foreman_fqdn=satellite.zed.corp
organization="Zed_Corp"
location="Paris"

[Europe:vars]
env=Production

[Europe]
host1
host2
```


Do not forget to create a satellite_credentials.yml using ansible-vault so you can store the Satellite 6 admin credentials
