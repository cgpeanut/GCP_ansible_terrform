# GCP_ansible_terrform
# Setup Ansible Environment: 

- simple two tier system with multiple web servers and a single load balancer.
- use ansible to install packages, manage configurations, patches, etc.

1.  Setup Inteventory
- Create sandbox servers thast will need to be configured and managed using Ansible.

- create aws key-pair (compute->EC2->Key Pairs) Name: ansible-key-pair (pem) use this to ssh to servers.
   - must be in the correct location and permissions set correctly. # chmod 400 ~/.ssh/ansible-key-pair.pem
   - create virtual machines lb, web1 and web2 in aws using cloud formation. (mgmt tootls) - cloudformation
     - create a new stack of webservers and a load balancer using provided cloudformation template
     - choose upload template to S3, Choose file setup-env.yml name the stack AnsibleStack NameofService: ansible-instances

   - login to lb: 
     - # ssh-keygen -t rsa
     - 172.31.36.254   7807d8804c1c.mylabserver.com web2
     - 172.31.44.216   7b64d772f71c.mylabserver.com b1
     - 172.31.37.145   ce61176c101c.mylabserver.com lb

1. Installing Ansible using trhe provisioned servers created in CloudFormation.

  -  Install Ansible on local control machine. This is where we will run Ansible commands and playbooks to manage our inventory servers. Linux based machine with python 3.x installed

    - # sudo easy_install pip
    - # sudo pip install ansible

2. Ensure End-to-End
  - Confirm that we have Ansible set up properly and are able to communicate with our inventory servers via SSH.

    # ssh -i ~/.ssh/ansible-key-pair.pem ec2-user@3.133.213.205 (lb)

3. Setup Inventory File:
    - need to give ansible a reference to our inventory servers we to execute commands on.
        - create an inventory which contains you inventory server information
        - 