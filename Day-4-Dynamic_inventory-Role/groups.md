THIS IS FOR HOST = GROUP NAME
---This group process I am doing in same ansible 
--If u have interest create a new resources doo same process until 
Aws_ec2.yml creation from here everything in changed
	Edit the aws_ec2.ymal
	Iam commented filters and added key_groups
```
---
plugin: amazon.aws.aws_ec2
regions:
  - us-east-1
    #filters:
  #  tag:Name:
    #    - dev
      #add multiple tag names here if required

keyed_groups:
  # add hosts to tag_Name_value groups for each aws_ec2 host's tags.Name variable.
  - key: tags.Name
    prefix: tag_Name_
    separator: ""
groups:
  # add hosts to the group dev if any of the dictionary's keys or values is the word 'dev'.
  development: "dev” in (tags|list)"
filters:
  tag:Name:
    - 'dev'
```