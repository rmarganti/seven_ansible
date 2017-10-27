# Seven-Ansible
------
Seven is a lamp stack provision using Ansible, Vagrant, and Virtual box. This doesn't include any additional bash or user config settings outside of whats provided in Vagrant's `centos/7` default box.

### Defaults
* PHP 7.1
* Apache/Httpd
* MariaDB
* git
* Redis
* Supervisiond
* NodeJs

Extras can be removed by modifying the `provisioning/default.yml` config.

### Dependecies 
* [Ansible](http://docs.ansible.com/ansible/latest/intro_installation.html)
* [Ansible Galaxy](http://docs.ansible.com/ansible/latest/galaxy.html)
* [Vagrant](https://www.vagrantup.com/)
* [VirtualBox](https://www.virtualbox.org/wiki/Downloads)

### Installation
Install all dependencies and pull down this repository.

```
$ git clone https://github.com/davidxhill/seven_ansible
```
Seven-ansible depends on multiple roles from Ansible’s official community hub and heavily on roles created by [geerlingguy](https://github.com/geerlingguy) . From the root level of this project, you will need to install the required roles from ansible-galaxy. These roles can be configured by reviewing their documentation by searching [here](https://galaxy.ansible.com/list#/roles?page=1&page_size=10).

```
$ ansible-galaxy install -r provisioning/requirements.yml
```

Once these requirements are completed the box can be created.

```
$ vagrant up
```

> Notes: there have been issues with authentication with vagrant on initial startup. If this happens, ensure the box is running and run `$ vagrant provision` to provision the box. Reload the box after provisioning `$ vagrant reload`

