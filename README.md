# Project1
First project 
Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![Cloud-Network-Diagram](https://user-images.githubusercontent.com/72894197/108268039-dae0f480-7120-11eb-82b0-855704ae507e.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _ file may be used to install only certain pieces of it, such as Filebeat.

[Filebeat.pdf](https://github.com/jjorns20/Project1/files/5998647/Filebeat.pdf)

This document contains the following details:

- Description of the Topologu

- Access Policies

- ELK Configuration

  - Beats in Use

  - Machines Being Monitored

- How to Use the Ansible Build

Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly reliable, in addition to restricting access to the network.

What aspect of security do load balancers protect? What is the advantage of a jump box?

  - Load Balancers protect against DOS attacks. The advantage of the jump box is to restrict access to the web vm's. 

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the actual machines and system logs.

What does Filebeat watch for?

  - Filebeat helps generate and organzie log files, it logs information about the file system and shows which files have changed and when.

What does Metricbeat record?

  - Metricbeat helps you monitor your servers by collecting metrics from the system and services running on the server.
  
The configuration details of each machine may be found below:


 | Name	       | Function	        | IP Address	| Operating System |
 |-------------|------------------|-------------|------------------|
 | Jump Box	   | Gateway	        | 10.0.0.16	  | Linux            |
 | WebVM-1     | DVWA Container		|	10.0.0.17   | Linux            |
 | WebVM-2     | DVWA Container   |	10.0.0.18	  | Linux            |
 | Elk         | Configuration VM | 10.2.0.4    | Linux            |
Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:

  - 76.94.242.109(My personal computer)

Machines within the network can only be accessed by accessing the DVWA container in the Jump Box..

Which machine did you allow to access your ELK VM? What was its IP address?

  - The only machines that can access the Elk server are my personal computer and the Jump Box VM through a peering connection.
  
A summary of the access policies in place can be found in the table below.

| Name	    | Publicly Accessible |	Allowed IP Addresses     |
|-----------|---------------------|--------------------------|
| Jump Box	| Yes/No	            | 10.0.0.16, 76.94.242.109 | 
| WebVM-1   | No                  | 10.0.0.17                |
| WebVM-2   | No                  | 10.0.0.18                |
|Elk        | No                  | 10.2.0.4                 |

Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...

 - You don't meed to install any other software or firewall ports on the client systems you want to automate.

The playbook implements the following tasks:

- Install Docker
- Download Image
- Configure container
- Create playbook to install container with docker and filebeat and metricbeat

The following screenshot displays the result of running docker ps after successfully configuring the ELK instance.

![docker_ps](https://user-images.githubusercontent.com/72894197/108277725-bdb32280-712e-11eb-9d3a-3731b8badce5.PNG)

Target Machines & Beats

This ELK server is configured to monitor the following machines:

  - WebVM-1 - 10.0.0.17
  - WebVM-2 - 10.0.0.18

We have installed the following Beats on these machines:

  - Filebeat and Metricbeat

These Beats allow us to collect the following information from each machine:

  - Filebeat monitors the log files or locations that you specify, collects log events, and forwards them either to Elasticsearch or Logstash. When filebeat starts logging data it looks like this:
  
  ![Filebeat_elk](https://user-images.githubusercontent.com/72894197/108281064-edb0f480-7133-11eb-81dc-37f76def1760.PNG)
  
  - Metricbeat periodically collect metrics from the operating system and from services running on the server. Metricbeat takes the metrics and statistics that it collects and ships them to the output that you specify, such as Elasticsearch or Logstash. Metricbeat will display information such as container CPU usage as follows:
  
  ![Metricbeat_elk](https://user-images.githubusercontent.com/72894197/108281320-61530180-7134-11eb-8acd-bfaca4d2d610.PNG)

Using the Playbook

In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:

Copy the filebeat-playbook.yml file to /etc/ansible/roles.

Update the filebeat-config.yml file to include the Elk server private IP.

Run the playbook, and navigate to kibana page to check that the installation worked as expected.

Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?

_Which URL do you navigate to in order to check that the ELK server is running?

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
