## Launch EC2s and install nginx server.

* Playbook : **playbooks/ec2-with-loop.yaml** 
### Create EC2 instance (Play)

1. Launch EC2 Instance
    * In one iteration of loop, Launch exact 2 EC2s with specified tag-name(**ansible-demo-single-0**) and wait until they are started. And loop count is 2. Meaning, this task will create total 4 aws EC2 instances. For one iteration the behaviour of the task is demonstrated in the form of example.
    * Example: 
        1. There are not existing stopped EC2s tag-name with **ansible-demo-single-(iteration)**.
            * The script will create new EC2s.
        2. There are two existing stopped EC2s tag-name with **ansible-demo-single-(iteration)**.
            * The script will restart these existing two EC2s.
        3. There are three existing stopped EC2s tag-name with **ansible-demo-single-(iteration)**.
            * The script will restart only two instances and terminate the third one. Why? Because we have instructed to launch exact 2 instances.
        4. There is one existing stopped EC2s tag-name with **ansible-demo-single-(iteration)**.
            * The script will restart existing stopped EC2 and launch one more cause we have instructed to launch exact 2 instances.
    * Reference: 
        * https://docs.ansible.com/ansible/latest/collections/amazon/aws/ec2_instance_module.html
        * https://docs.ansible.com/ansible/latest/playbook_guide/playbooks_loops.html
2. Wait till all instances are started.
    * Wait till all instances are started so we can make sure that all instances are started and fetch their metadata and ready to connect with them in the nexttask.
    * Reference: https://docs.ansible.com/ansible/latest/collections/amazon/aws/ec2_instance_module.html
3. Store Instance IDs in a Variable.
    * Store all instance ids of started instances.
    * Reference : https://docs.ansible.com/ansible/2.8/modules/set_fact_module.html
4. Final Instance IDs.
    * Just log the stored instance ids.
    * Reference: https://docs.ansible.com/archive/ansible/2.4/debug_module.html
5. Get Started Instances info
    * Get instance details of instances with instance IDs.
    * Reference: https://docs.ansible.com/ansible/2.9/modules/ec2_instance_info_module.html
6. Store Public IPs in a Variable.
    * Store public IPs of instances gathered from above task.
    * Reference : https://docs.ansible.com/ansible/2.8/modules/set_fact_module.html
7. Final Public IPs
    * Just log the stored public IPs.
    * Reference: https://docs.ansible.com/archive/ansible/2.4/debug_module.html
8. Add EC2 instance IP to Ansible hosts dynamically.
    * Add Public IPs of instances in host group.(ansible-demo-host)
    * Reference: https://docs.ansible.com/ansible/2.8/modules/add_host_module.html

### Run Tasks on EC2 Instance
1. Debug Information
    * Just log host variables.
    * Reference:
        * https://docs.ansible.com/ansible/latest/playbook_guide/playbooks_vars_facts.html
        * https://docs.ansible.com/archive/ansible/2.4/debug_module.html
2. Update apt
    * Update ubuntu repository
    * Reference: https://docs.ansible.com/archive/ansible/2.3/apt_module.html
3. Install nginx
    * Install nginx.
    * Reference: https://docs.ansible.com/archive/ansible/2.3/apt_module.html


