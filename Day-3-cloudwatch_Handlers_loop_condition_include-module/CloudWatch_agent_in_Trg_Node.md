# CloudWatch Agent 

- Attach iam role to ansible target node server for cloudwatch access 

- check connection and default key verification make false 

- create one playbook.yaml like 

```
- name: playbook
  hosts: all
  become: yes
  tasks:
    - name: Install CloudWatch agent
      yum:
        name: amazon-cloudwatch-agent
        state: present

    - name: Copy CloudWatch agent config
      copy:
        dest: /opt/aws/amazon-cloudwatch-agent/bin/config.json
        content: |
          {
            "logs": {
              "logs_collected": {
                "files": {
                  "collect_list": [
                    {
                      "file_path": "/var/log/*",
                      "log_group_name": "LOG-FROM-EC2",
                      "log_stream_name": "{instance_id}",
                      "retention_in_days": 30
                    }
                  ]
                }
              }
            }
          }

    - name: Start CloudWatch agent with config
      command: >
        /opt/aws/amazon-cloudwatch-agent/bin/amazon-cloudwatch-agent-ctl
        -a fetch-config
        -m ec2
        -c file:/opt/aws/amazon-cloudwatch-agent/bin/config.json
        -s

    - name: Ensure CloudWatch agent service is running
      systemd:
        name: amazon-cloudwatch-agent
        state: started
        enabled: yes
```

- Run this playbook and see in target node inside cloudwatch agent installed in all nodes

- Also check in cloudwatch logs are there.