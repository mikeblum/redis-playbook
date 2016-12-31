## redis-playbook

<img src="https://github.com/mikeblum/redis-playbook/raw/master/images/ansible.png" style="max-width: 150px"/>
---
<img src="https://github.com/mikeblum/redis-playbook/raw/master/images/redis.png"   style="max-width: 150px"/>

an Ansible playbook for deploying a secured and optimized Redis instance

Based originally on DigitailOcean's guide to deploying a Redis instance:

[How to install and configure redis on Ubuntu 16.04](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-redis-on-ubuntu-16-04)

This playbook looks to automate the tedious setup process by performing the following tasks:

- Update OS with apt-get
- Install Redis dependencies
- Install Redis from source (test, make)
- Configure and secure Redis-as-a-service
	- Create a `redis` user and group
	- Create data and logging directories
	- Enable Redis socket support (redis-cli -a redis -s /var/run/redis/redis.sock)

- Optimize Redis
	- Disable Transparent Huge Pages (THP) support 
	- Increase TCP backlog
	- Enable low-memory DB saves

Run `vagrant up` to provision a Redis instance available from your local machine.
