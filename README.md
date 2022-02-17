[![Opstree Solutions][opstree_avatar]][opstree_homepage]

[Opstree Solutions][opstree_homepage] 

   [opstree_homepage]: https://opstree.github.io/
   [opstree_avatar]: https://img.cloudposse.com/150x150/https://github.com/opstree.png


Osm Patch Mongo Role
====================

In this ansible role we can Patch and reboot the Mongo Cluster for new kernel update.

**Supported OS** 
====================

- Centos:7

Requirements
====================

The below plugin is  needed to run this ansible role.

* community.mongodb.mongodb_shell

```
ansible-galaxy collection install community.mongodb

```
Inventory
==================
```

An example inventory could be like this:-

[mongo_primary]
3.144.137.10

[mongo_secondary]
18.221.249.129
13.59.139.133

[mongo:children]
mongo_primary
mongo_secondary

[mongo:vars]
ansible_user=ec2-user
```

Example Playbook
==================
```yaml
---
- name: This is patching mongo role
  hosts: all 
  become: yes
  roles: 
    - role: mongo_patching

```


Usage
=============

Secrets.yml is required to run this ansible role. To Create
```
 ansible-vault encrypt_string 'USERNAME' --name 'login_user' >> secrets.yml
 ansible-vault encrypt_string 'PASSWORD' --name 'login_password' >> secrets.yml
```
To execute role

```shell
ansible-playbook -e "@secrets.yml" -i hosts sites.yml --ask-vault-pass 
```

Future Proposed Changes
========================
- Focus on some role Enhancement
- Patch mongo cluster for ubuntu distribution.

Reference
==========
*[Guid to patch mongo cluster](https://blog.opstree.com/2022/02/15/bigbulls-game-series-patching-mongodb-using-ansible/)*

Contributors
==================

**[Kritarth pant](kritarth.pant@opstree.com)**


 
