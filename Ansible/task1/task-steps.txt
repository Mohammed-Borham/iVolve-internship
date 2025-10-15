Lab 1: Initial Ansible Configuration and Ad-Hoc Execution


1. Install and configure Ansible Automation Platform on control node.
    
    $ sudo apt update
    $ sudo apt install software-properties-common
    $ sudo add-apt-repository --yes --update ppa:ansible/ansible
    $ sudo apt install ansible

2. Generate new key on control node.
    $ ssh-keygen -t rsa -b 4096

3. Transfer the public key into managed node using ssh-copy-id command.
    $ ssh-copy-id vagrant@192.168.1.10 # It ask for the managed node password
    $ ssh vagrant@192.168.1.10 # When you try to ssh agin it must not ask for password agin
4. Create inventory of a managed node.
    $ nano inventory # Create inventory file 
    # The content of the file must be like this 
      [managed_nodes]
      192.168.1.10 ansible_user=vagrant
5. Perform ad-hoc command (check disk space) to check functionality.
    $ ansible all -i ./inventory -m shell -a "df -h" # This command must return disk space of the managed node
