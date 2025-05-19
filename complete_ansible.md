# Ansible Hands-On
  This guide is about complete ansible hands-on practice.

## Steps 

 1. Create two EC2 instances - one for ansible server and another for target server
    
    ![Screenshot (143)](https://github.com/user-attachments/assets/7961e71e-e2f8-4499-a956-5981e0788633)

 2. SSH into ansible server and install ansible
    ```
    mkdir ansible
    cd ansible/
    sudo apt update
    sudo apt install ansible
    ansible --version
 3. Copy the SSH key to remote Host - If that doesn't work because of the public key error, you'll need to manually copy the key using another method
    ```
    ssh-keygen -t rsa -b 2048
    ssh-copy-id ubuntu@[target_ip]
    else
    local -> cat ~/.ssh/id_rsa.pub
    remote -> vim ~/.ssh/authorized_keys
 4. Passwordless Authentication
    ```
    ssh [target_ip]
 5. Come back and access inventory in ansible server
    ```
    Default directory for inventory file - /etc/ansible/inventory      
    cat /etc/ansible/inventory
 6. Open the inventory file and add the ip addresses of target_server for configuration management
    ```
    vim /etc/ansible/inventory
 7. Create sample file in the target servers
    ```
    ansible -i inventory all -m "shell" -a "touch devopsclass"
    ansible -i inventory all -m "shell" -a "nproc"
    ansible -i inventory all -m "shell" -a "df"
    ls -ltr
 8. Study about ansible modules & Create your first ansible playbook
    ```
    vim first-playbook.yml

    ---
    - name: Install Nginx
      hosts: all
      become: true

      tasks:
        - name: Install Nginx
          apt:
            name: nginx
            state: present
        - name: Start Nginx
          service:
             name: nginx
             state: started
 9. Run your first ansible playbook
     ```
     ansible-playbook -i inventory first-playbook.yml
     check on target server - sudo systemctl status nginx
     ansible-playbook -vvv -i inventory first-playbook.yml
 10. Configure Ansible role
     ```
     mkdir second-playbook
     cd second-playbook/
     ansible-galaxy role init kubernetes
     ls -ltr kubernetes/         
    
       
