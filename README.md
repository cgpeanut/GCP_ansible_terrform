# GCP_ansible_terrform
# Setup Ansible Environment:

1.  Setup Inteventory
- Create sandbox servers thast will need to be configured and managed using Ansible.

- create aws key-pair (compute->EC2->Key Pairs) Name: ansible-key-pair (pem) use this to ssh to servers.
   - must be in the correct location and permissions set correctly. # chmod 400 ~/.ssh/ansible-key-pair.pem
   - create virtual machines lb, web1 and web2 in aws using cloud formation. (mgmt tootls) - cloudformation
     - create a new stack of webservers and a load balancer using provided cloudformation template
     - 

   - login to lb: 
     - # ssh-keygen -t rsa
     - 172.31.36.254   7807d8804c1c.mylabserver.com web2
     - 172.31.44.216   7b64d772f71c.mylabserver.com web1
     - 172.31.37.145   ce61176c101c.mylabserver.com lb
1. Installing Ansible
  -  Install Ansible on local control machine. This is where we will run Ansible commands and playbooks to manage our inventory servers.
3. Ensure End-to-End
  - Confirm that we have Ansible set up properly and are able to communicate with our inventory servers via SSH.

- simple two tier system with multiple wev servers and a single load balancer.
- use ansible to install packages, manage configurations, patches, etc.
