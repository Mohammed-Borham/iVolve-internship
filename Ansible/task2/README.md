Lab 2: Automated Web Server Configuration Using Ansible Playbooks

1. Write an Ansible playbook to automate the configuration of a web server
    # Make the inventory file 
      [Nginx-server]
      192.168.1.10 ansible_user=vagrant
    # create playbook.yml which have the Nginx configuration
---
- name: Configure Nginx Web Server
  hosts: Nginx-server
  become: yes   # run as root (using sudo)

  tasks:
    - name: Install Nginx
      apt:
        name: nginx
        state: present
        update_cache: yes

    - name: Start and enable Nginx service
      service:
        name: nginx
        state: started
        enabled: yes

    - name: Deploy custom index.html
      copy:
        content: |
          <html>
          <head><title>Ansible Web Server</title></head>
          <body style="background-color:#1e1e2f; color:#fff; font-family:sans-serif;">
          <h1>Hello there its Borham</h1>
          <h2>Welcome from Nginx</h2>
          <p>This page was automatically configured using Ansible.</p>
          </body>
          </html>
        dest: /var/www/html/index.html
        owner: www-data
        group: www-data
        mode: '0644'

2. Install Nginx & Customize the web page.
    # After writting the playbook file execute the following command
      $ ansible-playbook -i inventory playbook.yml 
    # The playbook contain the installation of Nginx server and also have the content of index.html file

3. Verify the configuration on managed node.
    # From the managed node 
        $ curl localhost:80 
    # it return the content of the index.html file 
    # From the contoller node 
        $ ssh vagrant@192.168.1.10
        $ curl localhost:80
    #From the browser write this url
        $ http://192.168.1.10:80


