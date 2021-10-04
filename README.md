## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

- ~/Projects/ELK_Project/Images/ELKDiagram.png

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the install_elk.yml file may be used to install only certain pieces of it, such as Filebeat.

  - [install_elk.yml]

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting access to the network.
- What aspect of security do load balancers protect? What is the advantage of a jump box? Load balancers protect against DDoS attacks. Jump gives the user access from a single nod that can be secured and monitored. 

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the log and system data.
- What does Filebeat watch for? Filebeat is a shipper for forwarding and centralizing log data. 
- What does Metricbeat record? Metricbeat takes the metrics and statistics collected and ships them to a specified output. 

The configuration details of each machine may be found below.

| Name     | Function |         IP Address       | Operating System |
|----------|----------|--------------------------|------------------|
| Jump Box | Gateway  | 10.0.0.4(52.160.68.11)   | Linux            |
| Web 1    | DVWA     | 10.0.0.5                 | Linux            |
| Web 2    | DVWA     | 10.0.0.6                 | Linux            |
| ElkVm    | Server   | 10.1.0.4(13.68.189.8)    | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the jump-Box-Provisioner machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- Access to the jump-Box machine is only allowed from 72.19.168.165 (Local Host)

Machines within the network can only be accessed by the jump-Box-Provisioner.
- Which machine did you allow to access your ELK VM?
-- jump-Box-Provisioner 
- What was its IP address?
-- 10.0.0.4(Private) 

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 72.19.168.165        |
| ElkVm    | No                  | 10.0.0.4             |
| Web 1    | No                  | 10.0.0.4             |
| Web 2    | No                  | 10.0.0.4             |
### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- What is the main advantage of automating configuration with Ansible? 
  The main advantage would be using YAML playbooks for the configuration, automation, and management of environments.  

The playbook implements the following tasks:
- In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- ... ssh into jump-Box with (ssh azadmin@52.160.68.11) and then start and attach to ansible container with (sudo docker start stupefied_ride)/(sudo docker attach stupefied_ride)
- ... Create playbook file with (touch /etc/ansible/install_elk.yml) and edit the file with the appropriate tasks to run when the playbook launches.  
- ... Run the playbook with (ansible-playbook /etc/ansible/install_elk.yml)
- ... ssh into the ElkVm with (ssh azadmin@10.1.0.4) and verify that the elk container has been launched with (docker ps).

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

- ~/Projects/ELK_Project/Images/ElkVm_~.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- (10.0.0.5)Private (10.0.0.6)Private

We have installed the following Beats on these machines:
- Filebeat and Metricbeat installed and operating successfully. 

These Beats allow us to collect the following information from each machine:
- Filebeat was installed to collect log data about the file system. 
- Metricbeat was installed to collect machine metrics such as uptime. 

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the install_elk.yml file to /etc/ansible.
- Update the /etc/ansible/hosts file to include webservers and elk.
- Run the playbook, and navigate to the elk machine to check that the installation worked as expected.

- _Which URL do you navigate to in order to check that the ELK server is running?
- http://[your.VM.IP]:5601/app/kibana.
- cp install_elk.yml /etc/ansible
- nano /etc/ansible/hosts and put both elk and webservers in brackets and under them add (yourmachinesIP) ansible_python_interpreter=/usr/bin/python3
- run the playbook with ansible-playbook /etc/ansible/install_elk.yml 
- ssh username@privateIP and run sudo docker ps 
- If containers return congratulations. 
