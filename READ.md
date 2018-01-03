

###clone repo:
$ ansible-playbook git_clone.yml

###install and configure nginx:
$ ansible-playbook -i inventory nginx_install.yml --sudo

###install node:
$ ansible-playbook -i inventory node_install.yml --sudo

###run node app:
$ ansible webservers -i inventory -m shell -a "/usr/bin/node /home/ubuntu/hello-world-node-express/app.js"

###install rsyslog:
$ ansible-playbook -i inventory rsyslog_install.yml 

###make sure iptables isn't running:
$ ansible webservers -i inventory -m shell -a "ufw allow 514/tcp" --sudo
