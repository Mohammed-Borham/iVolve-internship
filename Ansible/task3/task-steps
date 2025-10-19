Lab 3: Structured Configuration Management with Ansible Roles


1. Create Ansible roles for configuring Docker, Kubernetes CLI ‘kubectl’, and Jenkins.
	#By using ansible-galaxy to create roles automatically
		$ansible-galaxy init roles/docker
                $ansible-galaxy init roles/kubectl
                $ansible-galaxy init roles/jenkins

	#Then write the main.yml for every role

3. Write Ansible playbook to run the created roles.
        #Write the main playbook and inventory
	#Run the main playbook 
		ansible-playbook -i inventory site.yml 

4. Verify the installation on managed node.
	#Using the following commands to verify the installation
		$ansible all -i inventory -m shell -a "docker --version"
		$ansible all -i inventory -m shell -a "kubectl version --client"
		$ansible all -i inventory -m shell -a "systemctl status jenkins | grep Active"

