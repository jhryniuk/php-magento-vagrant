Vagrant machine with Magento2 Nginx and PHP 7
=============================================
### Required programs:
* Newest version Virtualbox, which you can download from: [Click here.](https://www.virtualbox.org/wiki/Downloads)
* Newest version of Vagrant: [Click here.](https://www.vagrantup.com/downloads.html)

### Getting started:
Download project:
* To download this project use command: `git clone [link from github] vagrant`.
* After downloading you should move `vagrant` folder to project witch require this machine.
* Add `vagrant` into file `.gitignore` of project.

Before you start the machine please look into file vars.yml and set the variables.
#### Make sure that you set ``github_token`` variable.

### Run virtual machines:

```bash
cd vagrant
vagrant up
#log in to vm 
vagrant ssh
```

Put this line into ``/etc/hosts``: ``10.0.0.200  [domain_name] ``

### Shutdown VM
After finish work you should turn off virtual machine using ``vagrant halt`` command
