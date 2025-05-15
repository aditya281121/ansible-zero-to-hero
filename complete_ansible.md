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
 5. Passwordless Authentication
    ```
    ssh [target_ip]
 6. Come back and access inventory in ansible server
    ```
    Default directory for inventory file - /etc/ansible/inventory      
    cat /etc/ansible/inventory
    nano /etc/ansible/inventory

    
    
       
