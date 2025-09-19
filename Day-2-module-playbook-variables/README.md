# Modules 

- Module means directly given instruction by ansible 
- ad-hoc coomand means run the linux commands directly 



----ping module-------
ansible -i inventory all -m ping 

-----stat module ----
ansible -i inventory all -m stat -a "path=/var/www/html"

----------user----------

ansible -i inventory all -m user -a "name=naresh" -b

-----------setup--------
ansible -i inventory all -m setup

---------------file------------
ansible -i inventory all -m file -a "name=demo state=touch"

---------------copy-------------
ansible -i inventory all -m copy -a "src=file1  dest=~"


------yum or apt module ----- ##Very ImP

(basic state's
name = (httpd install)
               state=latest
               state=present
               state=absent )

ansible all -m yum -a "name=httpd state=latest" -b
ansible all -m yum -a "name=httpd state=present" -b
ansible all -m yum -a "name=httpd state=absent" -b

name = systemctl or service              
               state=stopped
               state= started
               state=restrted

- Download from internet by using get_url module 

- ansible web -m get_url -a "url=https://dlcdn.apache.org/tomcat/tomcat-9/v9.0.106/bin/apache-tomcat-9.0.106.zip dest=/opt/apache-tomcat-9.0.106.zip mode=0644"

               


Examples :
ansible -i inventory all -m yum -a "name=httpd state=latest" -b     #to install httpd

ansible -i inventory all -m service -a "name=httpd state=started" -b     #to start service

ansible -i inventory all -m service -a "name=httpd state=stopped" -b     #to stop service

ansible -i inventory all -m yum -a "name=httpd state=absent" -b     #to uninstall service

ansible -i inventory all -m service -a "name=httpd state=restarted" -b     #to restart service

ansible all -m systemd -a "name=httpd" -b  to know the status module


# Playbook

- Many commands run a same time 
- It is a text file where we can add all instruction to execute.

- For run playbook.yaml 

```
ansible-playbook <playbook.yaml name> 
```

- copymodeule : 

  - copymodeule means copy file from source server to target server 

# Tags :

  - yaml inside many task is there how to run specific task or block specific task.
  - By using of tags

# Variables : 

  - variables are using for write variablised the task inside directly call the variable insted of write all name and services.