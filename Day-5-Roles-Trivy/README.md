# Trivy

- Go to trivy website and 

- trivy is a vulnerebility scanner which is scan vulnerebility and bug inside the images

- install trivy: 

```
sudo rpm -ivh https://github.com/aquasecurity/trivy/releases/download/v0.48.3/trivy_0.48.3_Linux-64bit.rpm

trivy image <image name>

trivy image nginx

trivy image --format json -o trivy_report.json nginx:latest

jq . trivy_report.json
```


# Roles 

- ansible role ls like helm of kubernetes

-Ansible Roles provide a structured way to organize tasks, templates, files, and variables. This structure makes it easier to manage complex automation setups, as everything related to a specific role is contained within its directory


- install role or create role : 
```
ansible-galaxy init <rolename>
```

- install tree and check the role folder structure.

- all yaml containes in the ansible role inside a main.yaml inside 

- main.yaml call the child task module and run one by one so we can control the child  task by main.yaml

Role Name
=========

A brief description of the role goes here.

Requirements
------------

Any pre-requisites that may not be covered by Ansible itself or the role should be mentioned here. For instance, if the role uses the EC2 module, it may be a good idea to mention in this section that the boto package is required.

Role Variables
--------------

A description of the settable variables for this role should go here, including any variables that are in defaults/main.yml, vars/main.yml, and any variables that can/should be set via parameters to the role. Any variables that are read from other roles and/or the global scope (ie. hostvars, group vars, etc.) should be mentioned here as well.

Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: username.rolename, x: 42 }

License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).