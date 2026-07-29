
# Automated Web Server Configuration Using Ansible Playbooks
This lab demonstrates automating web infrastructure deployment using Ansible Playbooks. It covers writing a structured YAML playbook to automate package management, service orchestration, and custom file deployment for an Nginx web server, followed by verifying the web server response via Ansible ad-hoc execution.

---

## Step 1: Create the Ansible Playbook
Create a new file named `webserver.yml` with the following configuration:

<img src="Screenshots/1.png" alt="1" width="500">


## Step 2: Execute the Playbook
Run the playbook against the inventory using ansible-playbook:

<img src="Screenshots/2.png" alt="1" width="800">

## Step 3: Verify Web Server Configuration
Verify that Nginx is active and serving the customized landing page by executing an HTTP GET request through an Ansible Ad-Hoc command:

<img src="Screenshots/3.png" alt="1" width="800">
