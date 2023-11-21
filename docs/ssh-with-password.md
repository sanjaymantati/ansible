## Connect to host and execute commands with sudo user.



### Steps
1. playbook:ssh-connection-with-password.yaml
2. Add inventory in /etc/ansible/hosts.  
   * Reference : https://docs.ansible.com/ansible/latest/inventory_guide/intro_inventory.html#inventory-basics-formats-hosts-and-groups
```text
...


[dev1060system]
192.168.10.39

...
```
3. Now we are using ssh with password we need to disable host key check.
    * Reference : https://docs.ansible.com/ansible/latest/inventory_guide/connection_details.html
```text
...

[defaults]
host_key_checking = False

...
```

4. Execute below command 
    * Reference : https://docs.ansible.com/ansible/latest/inventory_guide/connection_details.html
```shell

$ ansible-playbook ssh-connection-with-password.yaml --ask-pass --ask-become-pass

```