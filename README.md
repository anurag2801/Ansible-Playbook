# Ansible-Playbook

This Ansible playbook automates the installation of Docker, Docker Compose, and AWS CLI on a remote machine. Before running the playbook, ensure you have the following prerequisites and steps configured:
Prerequisites

    Remote Machine (Target Host)
        Ensure the remote machine (where you want to install Docker, Docker Compose, and AWS CLI) is accessible over SSH.
        Note down the IP address or hostname of the remote machine.

    Ansible Control Machine
        Install Ansible on your local or control machine where you will execute the playbook.
        Ensure SSH connectivity is established between the Ansible control machine and the remote machine.

    Ansible Inventory File
        Update the /etc/ansible/hosts file on your Ansible control machine to include the IP address or hostname of the remote machine under a suitable group. Example:

        ini

        [remote]
        3.110.178.58 ansible_user=ubuntu

        Replace 3.110.178.58 with your remote machine's IP address and ubuntu with the appropriate SSH username.

    SSH Key Pair
        Ensure you have an SSH key pair configured on the Ansible control machine.
        Add the SSH public key (id_rsa.pub) to the ~/.ssh/authorized_keys file on the remote machine for passwordless SSH access.

Usage

    Clone the Repository
        Clone this GitHub repository to your Ansible control machine where you have Ansible installed.

        bash

    git clone git@github.com:anurag2801/jenkin-docker-demo.git
    cd jenkin-docker-demo

Update Playbook Variables (Optional)

    Modify the awsdocker.yaml playbook if necessary to adjust variables like AWS CLI version, Docker version, etc.

Run the Ansible Playbook

    Execute the Ansible playbook using the following command:

    bash

    ansible-playbook -i /etc/ansible/hosts awsdocker.yaml

    Adjust the -i parameter if your inventory file is located elsewhere.

Verify Installation

    After the playbook execution completes successfully, verify that Docker, Docker Compose, and AWS CLI are installed on the remote machine:

    bash

        ssh ubuntu@3.110.178.58
        docker --version
        docker-compose --version
        aws --version

Notes

    Ensure that your Ansible control machine has sufficient network connectivity to reach the remote machine.
    Troubleshoot any connectivity or permission issues related to SSH keys, firewall rules, or user permissions as needed.

By following these steps, you can automate the installation of Docker, Docker Compose, and AWS CLI on your remote machine using Ansible.
