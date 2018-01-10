App can be reached at http://ec2-34-234-71-240.compute-1.amazonaws.com/

Deployed using ansible 2.0.0.2

Ansible Controller host: ec2-107-20-128-13.compute-1.amazonaws.com

### Using the Ansible Controller host, use this command to run the webserver:
$ ansible webservers -i inventory -m shell -a "/home/ubuntu/hello-world-node-express/startnodeapp.sh"

## Steps taken to configure the webserver:

### clone repo:
$ ansible-playbook git_clone.yml

### install and configure nginx:
$ ansible-playbook -i inventory nginx_install.yml --sudo

### install node:
$ ansible-playbook -i inventory node_install.yml --sudo

### run node app:
$ ansible webservers -i inventory -m shell -a "/usr/bin/node /home/ubuntu/hello-world-node-express/app.js"

The following shell script was added to crontab to have it start up automatically upon reboot: /home/ubuntu/hello-world-node-express/startnodeapp.sh

## install rsyslog:
$ ansible-playbook -i inventory rsyslog_install.yml

### make sure iptables isn't running:
$ ansible webservers -i inventory -m shell -a "ufw allow 514/tcp" --sudo

### Remote logging can be viewed on ec2-107-20-128-13.compute-1.amazonaws.com:/var/log/syslog

## MySQL DB installed on instance: ec2-34-229-59-133.compute-1.amazonaws.com 
```
mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| mysql              |
| performance_schema |
| tech_challenge     |
+--------------------+
```
creds provided to user ubuntu:
mysql> grant ALL on tech_challenge.* to 'ubuntu'@'localhost' identified by 'passwd';

user ubuntu can now log into to db:
```
ubuntu@ip-172-31-39-103:~$ mysql -u ubuntu -p
Enter password:
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 52
Server version: 5.5.58-0ubuntu0.14.04.1 (Ubuntu)

```
### Unfinished ELK cluster can be found on http://ec2-54-173-129-114.compute-1.amazonaws.com/ 
