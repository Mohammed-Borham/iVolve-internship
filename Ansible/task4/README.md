Lab 4: Securing Sensitive Data with Ansible Vault

1. Write Ansible playbook to automate the following tasks:
* Install MySQL. 
* Create iVovle database.
* Create user with all privileges on iVolve DB. 
	#First create inventory file with managed node ip
	#Then create playbook.yml to install sql-server, ensure that it is running, create mysql-db, and db-user

2. Use Ansible Vault to encrypt sensitive information such as database user password.
	#First create /vars to add vault.yml 
	#Then add the db-vars in the vault.yml
	#After that use $ansible-vault encrypt vars/vault.yml >>add encryption pass
	#Finally i modified the playbook.yml to define vault.yml on it


3. Validate DB on managed node by connect to database using the created user and listing databases.
	# ssh on managed node to ensure that database listed and user created 

	### Output is in the screen in the same dir
