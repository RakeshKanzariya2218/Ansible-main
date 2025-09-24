# Vault 

- Ansibl vault is like lock of playbook if we encrypt the playbook and keep in vault then no anyone can run that playbook.

- If we want to run then need username and password and make it again decrypt format 
```
ansible-vault create secret.yaml
```

- need to provide password

- then go to vi editor and place any yaml file and run 

- after that try to edit or read the yaml but we are unable to read due to encryption applies

- if we want to modify the yaml give below command 
```
ansible-vault edit secret.yaml
```
and enter given password 
  
if we want want decrypt the password
```
ansible-vault decrypt secret.yaml
```
and give password

  if want to encrypt the password 
  ```
ansible-vault encrypt secret.yaml
```
to provide secure 