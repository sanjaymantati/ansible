## Connect to host and execute commands with sudo user.



### Steps
1. playbook:ssh-connection-with-ssh-key.yaml
2. Add inventory in /etc/ansible/hosts with ssh key file path.
   * Reference : 
     * https://docs.ansible.com/ansible/latest/inventory_guide/intro_inventory.html#intro-inventory
     * https://docs.ansible.com/ansible/latest/inventory_guide/connection_details.html#setting-up-ssh-keys
   * Reference : 
```text
...


[dev1060system]
192.168.10.39   ansible_ssh_private_key_file=/home/dev1055/ansible/office-pc-pem.pem

...
```

3. Execute below command 
    * Reference : https://docs.ansible.com/ansible/latest/inventory_guide/connection_details.html
```shell

$ ansible-playbook ssh-connection-with-ssh-key.yaml --ask-become-pass

```
* Now, if you want to specify ssh key file in command line then you can do it in below fashion and no need to specify ssh file path in /etc/ansible/hosts file.

```shell
$ ansible-playbook ssh-connection-with-ssh-key.yaml  --ask-become-pass  --private-key=/home/dev1055/ansible/office-pc-pem.pem

```


#### Caveats
1. You may face the ssh "permissions are too open" issue. How to resolve it? Well, follow below stackoverflow.
   * https://stackoverflow.com/questions/9270734/ssh-permissions-are-too-open