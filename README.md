# R-Ralph
Project 1 BootCamp CYbersecurity
#
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

https://github.com/Ralph-Ramlal/R-Ralph/commit/dcf6834f5cfdc46259c3be6b582a87b82149d89b#commitcomment-60702475

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook file may be used to install only certain pieces of it, such as Filebeat.

 https://github.com/Ralph-Ramlal/R-Ralph/blob/bd7ae2a38ba2486d46647649f652362d0fa18d3c/Diagrams/filebeat-playbook.yml

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly responsive, in addition to restricting acess to the network.
What aspect of security do load balancers protect? A load balancer can add additional layers of security to your website without any changes to your application. What is the advantage of a jump box ?A jump server, jump host or jump box is a system on a network used to access and manage devices in a separate security zone. 

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the log and system traffic.
What does filebeat watch for? Filebeat is a lightweight shipper for forwarding and centralizing log data
What does Metricbeat record? Metricbeat takes the metrics and statistics that it collects and ships them to the output that you specify, such as Elasticsearch or Logstash. Metricbeat helps you monitor your servers by collecting metrics from the system and services running on the server, such as: Apache.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name    |            Function            |      IP Adress            |      IP Adress         |
|---------|--------------------------------|---------------------------|------------------------|
| Jump Box| Gateway                        |  10.0.0.1 /20.124.122.237 | Linux Ubuntu 18.04.01  |          
| Web-1   | Webserver used to run DVWA     |  10.0.0.7                 | Linux Ubuntu 18.04.01  |       
| Web-2   | Webserver used to run DVWA     |  10.0.0.8                 | Linux Ubuntu 18.04.01  |
| Elk     | Run Elk containers and Kibana  |  10.4.04 / 52.229.102.65  | Linux Ubuntu 18.04.01  | 

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump-Box Provisioner machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
73.115.160.129

Machines within the network can only be accessed by the Jump-Box Provisoner VM.
The ELK machine can be accesssed by the Jump-Box-Provisioner. IP address 10.4.04

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible |      Allowed IP Addresses            |
|----------|---------------------|--------------------------------------|
| Jump Box | Yes                 | Workstation Public IP 73.115.160.129 |
| Web-1    | No                  |  Jump-Box IP 10.0.07                 |
| Web-2    | No                  |  Jump-box IP 10.0.08                 |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because servcies running can be limited, system installation and update can be streamlined, and processes become more replicable.

What is the main advantage of automating configuration with Ansible? - Ansible is a configuration management platform that automates storage, servers, and networking. When you use Ansible to configure these components, difficult manual tasks become repeatable and less vulnerable to error.

The playbook implements the following tasks:

- Download and launch Elk container. The Elk docker will be downloaded and launched on boot
- Configured to set up the ELK stack together with Metricbeat for server monitoring.
- The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

https://github.com/Ralph-Ramlal/R-Ralph/commit/0a676de08d43cffe8840daa51170233a77572067#r60781270

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
Web-1 (IP 10.0.0.7) Web-2 (IP 10.0.0.8)

We have installed the following Beats on these machines:
Filebeat monitors (Web-1, Web-2) the log files or locations that you specify, collects log events, and forwards them either to Elasticsearch or Logstash for indexing.
Metricbeat takes the metrics and statistics that it collects and ships them to the output that you specify, such as Elasticsearch or Logstash.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the filebeat-config.yml file to /etc/ansible/files/filebeat-config.yml 
- Update the filebeat-config.yml file to include host 10.4.0.4 username"elastic" password "changeme"
- and setup "kibana" host to "10.4.0.4
- Run the playbook, and navigate to http://[your.ELK-VM.External.IP]:5601/app/kibana to check that the installation worked as expected, click "Check Data"

- _Which file is the playbook? 
- filebeat-playbook.yml

-Where do you copy it?
/etc/ansible/filesbeat-playbook.yml

- _Which file do you update to make Ansible run the playbook on a specific machine?
- /etc/ansible/hosts

 How do I specify which machine to install the ELK server on versus which to install Filebeat on?
 Web-1 and Web-2 both private IP adress to the file host under [webserver] and  adding the private Ip adress on the ELK server
 
- Which URL do you navigate to in order to check that the ELK server is running?
  http://20.122.9.18:5601/app/kibana#/home

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._

Playbookfile
filebeat-playbook.yml





