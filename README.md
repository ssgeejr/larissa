# larissa
Ansible playbooks for windows patching/updating



For installing agents: 
https://www.orb-data.com/mass-deploy-zabbix-agent-using-ansible/


For windows agent: 
https://github.com/dj-wasabi/ansible-zabbix-agent#windows-variables

Another windows agent example: 
https://piccadil.medium.com/ansible-playbook-for-managing-windows-linux-and-snmp-zabbix-agents-d28d09e2109b
https://github.com/piccadil/zabbix-agent

Install Git for Debian 
https://yasha.solutions/install-docker-on-debian-with-ansible/


#### Setting up Debian 11
```
#!/bin/bash

adduser --disabled-password --gecos "" ansible
cd /home/ansible
mkdir .ssh

cat << EOF > /home/ansible/.ssh/config
Host *
    StrictHostKeyChecking no
	
Host *
    IdentityFile ~/.ssh/ansible.admin
EOF

cat << EOF >> /home/ansible/.ssh/authorized_keys
<ENTER_YOUR_PUBLIC_SSH_KEY_HERE>
EOF

chown -R ansible.ansible /home/ansible/.ssh
chmod 600 /home/ansible/.ssh/*
chmod 700 /home/ansible/.ssh

echo "%ansible ALL=(ALL) NOPASSWD: LOG_INPUT: ALL"  > /etc/sudoers.d/admin-ansible

apt-get update

apt-get install -y lvm2 wget curl git python3-pip python3-dev build-essential 

curl -fsSL https://get.docker.com/ | sh

systemctl start docker
systemctl enable docker
usermod -aG docker ansible

pip3 install -U pip

pip install -U docker-compose


```