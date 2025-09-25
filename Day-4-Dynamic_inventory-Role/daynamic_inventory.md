# Dynamic inventory 

- Dynamic inventory menas inside ansible master node configure all target node tags
- because when asg create new server with same tag then connection should not be loss

- Insted of hardcode ip we configure tag of the target node so no problem when asg create new server.

# process 

- install dependencies in master node
```
yum install python3-pip -y
sudo python get-pip.py 
sudo pip install boto3
sudo pip show boto3
```

- make sure connection master node to target node by ssh--keygen 

- go to ansible config file and add the data : to define ansible default action 
```
vi /etc/ansible/ansible.cfg
[defaults]
enable_plugins = aws_ec2     # it will firt check plugins 
inventory =./aws_ec2.yml     # after that go inside this inventory file 
host_key_checking = False    # key verificatioon in failse 
``

- Create tag file in the ansible main directory to enable pluggins 
```
	sudo vi /etc/ansible/aws_ec2.yml
    ```
- paste the below mater
```
plugin: amazon.aws.aws_ec2
regions:
  - us-east-1
filters:
  tag:Name: 
    - dev
      #add multiple tag names here if required
```

- create the sample playbook in the same ansible directory 

```
- name: first playbook
  hosts: all
  become: yes
  tasks:
    - name: install httpd software
      yum:
        name: httpd
        state: latest
    - name: start web server
      service:
        name: httpd
        state: started
```

- Run the playbook and delete ec2 - create by asg and like that ansible connect new ec2 by the tags .