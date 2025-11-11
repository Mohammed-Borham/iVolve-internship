Lab 5: Automated Host Discovery with Ansible Dynamic Inventory


1.Create AWS EC2 with tag name:ivolve.
  # By useing AWS console, I create ec2-instance with ivolve name
        ** Create new vpc to the project with public sub
        ** Create the instance with public ip
        ** Using SG to open access to ssh and http ports

2.Set up Ansible dynamic inventory to automatically discover and manage running EC2.
  # First install all requirment 
        ** install python3 >> to use pip
        ** activate venv >> to install boto3, botocore, and ansible
        ** install aws plugins
  # Second create ec2_aws.yml 
        ** useing amazon.aws.ec2 plugin and add tag:Name: ivolve >> which i use with the ec2 creation
        ** use compse to define ansible user and host to access ec2
        ** use ansible.cfg to add collection path >> where ansible is installed


list the target hosts using ansible inventory command.
Run any playbook or ad-hoc command to verify.
