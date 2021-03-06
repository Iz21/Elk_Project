## Automated ELK Stack Deployment
The files in this repository were used to configure the network depicted below.
![TODO: Update the path with the name of your diagram](./Images/Azure%20Cloud%20Network%20diagram%20Private%20-%20Week%2013_IA-Page-1.drawio.png) 

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the Cloud Network Diagram for ELK deployment file may be used to install only certain pieces of it, such as Filebeat.
[ELK-install](https://github.com/Iz21/Elk_Project/blob/main/Ansible/ELK-install.yml)
This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build
### Description of the Topology
The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.
Load balancing ensures that the application will be highly available, in addition to restricting access to the network.

What aspect of security do load balancers protect? 

- Load Balancers protect an organization's servers from potential incoming malicious traffic.

- Some examples include daily rule updates, username and password requests and verification, and DDoS detection. 

What is the advantage of a jump box?

- A jump box acts as a single node entry point for a user to gain access  

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system traffic.
What does Filebeat watch for?
- Filebeat monitors log files or specified locations, collects log events and forwards them for indexing based on how it has been configured

What does Metricbeat record?
- Metricbeat periodically collects metrics from OS or any services running on a server, and then ships these metrics to any output that it is configured for. 


The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table

| Name     | Function   | IP Address  | OS     |
|----------|------------|-------------|--------|
| JumpBox  | Gateway    | 10.0.0.4    | Linux  |
| Web-1    | Webserver  | 10.0.0.5    | Linux  |
| Web-2    | Webserver  | 10.0.0.6    | Linux  |
| ELK-VM   | Webserver  | 10.1.0.4    | Linux  |

### Access Policies
The machines on the internal network are not exposed to the public Internet. 
Only the JumpBox Provisioner machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:

5601 Kibana Port

Machines within the network can only be accessed by JumpBox Provisioner.
- Which machine did you allow to access your ELK VM? What was its IP address?_
A summary of the access policies in place can be found in the table below

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 10.0.0.4             |
| Web-1    | No                  | 10.0.0.4             |
| Web-2    | No                  | 10.0.0.4             |
| ELK-VM   | No                  | 10.0.0.4             | 

### Elk Configuration

https://github.com/Iz21/Elk_Project/blob/main/Ansible/Pentest.yml

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...

What is the main advantage of automating configuration with Ansible?
- Flexibility, scalability and speed of enabling applications
- The different applications of Ansible include provisioning, configuration management, deploying applications, security and compliance, and orchestration. (https://www.whizlabs.com/blog/ansible-advantages-and-disadvantages/)

The playbook implements the following tasks:

In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- Install Docker
- Install Elasticsearch
- Install Logstash
- Install Kibana
- Install Beats

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.
![Docker_ps](Images/docker_ps.png)
### Target Machines & Beats
This ELK server is configured to monitor the following machines:

| Web-1 | 10.0.0.5  |
|-------|-----------|
| Web-2 | 10.0.0.6  |

We have installed the following Beats on these machines:

`Filebeat` `Metricbeat`

These Beats allow us to collect the following information from each machine:
- In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc.

https://github.com/Iz21/Elk_Project/blob/main/Ansible/Metricbeat-playbook.yml

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 
SSH into the control node and follow the steps below:
- Copy the ssh-keygen file to ssh public key.
- Update the security rule file to include the IP Address. 
- Run the playbook, and navigate to `ELK-VM Public IP:5601/app/kibana` to check that the installation worked as expected.
_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
- _Which URL do you navigate to in order to check that the ELK server is running?
_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._

