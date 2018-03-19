# AnsibleTowerInstallation

# create instance with 2 core and 4 GB RAM on any cloud provider 
# ssh into that machine
# lets install latest ansible with below commands 
# lets change user with 
sudo su

# Install Ansible 2.4
 sudo apt-get update
 sudo apt-get install software-properties-common
 sudo apt-add-repository ppa:ansible/ansible
 sudo apt-get update
 sudo apt-get install ansible
 
# chek ansible version you got with below command

ansible --version 

Now lets install latest ansible tower 

Read through this doc http://docs.ansible.com/ansible-tower/latest/html/quickinstall/prepare.html

# Download tower setup 
http://releases.ansible.com/ansible-tower/setup/ 

scroll down copy link of latest and then on terminal
 wget http://releases.ansible.com/ansible-tower/setup/ansible-tower-setup-latest.tar.gz
 tar -xzvf ansible-tower-setup-latest.tar.gz
 
 cd ansible-tower-setup-3.2.3/

make changes to inventory file as below /replace directly with below file  
---------------------------------
[tower]
localhost ansible_connection=local

[database]

[all:vars]
admin_password='admin'
ansible_host='localhost'
pg_host='127.0.0.1'
pg_port='5432'

pg_database='awx'
pg_username='awx'
pg_password='admin'

rabbitmq_port=5672
rabbitmq_vhost=tower
rabbitmq_username=tower
rabbitmq_password='admin'
rabbitmq_cookie=cookiemonster

# Needs to be true for fqdns and ip addresses
rabbitmq_use_long_name=false

# Isolated Tower nodes automatically generate an RSA key for authentication;
# To disable this behavior, set this value to false
# isolated_key_generation=true

--------------------------------------

execute setup.sh now 

root@instance-2:/home/ubuntu/ansible-tower-setup-3.2.3# ./setup.sh

This will execute tower playbook and install ansible tower 
Tower will be accessible on port 443 

For first time it will ask you for license key . once you login it will prompt for you . select request license key and fill information to get free one
it will not require any credit card details 

you will recieve key in email. upload same to tower. you will start using ansible tower then


 
 
 
 






