# Elk-Stack-Project-1
This is a cloud monitoring system I've set up by configuring an ELK stack server. 

## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

Images/Elkstack/Jumpbox Project1.drawio

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the yml and config file may be used to install only certain pieces of it, such as Filebeat.

  - /etc/ansible/ansible.cfg


This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly answer, in addition to restricting traffic to the network.
- What aspect of security do load balancers protect?
  Answer: Web Traffic, Web Security, Availability

  What is the advantage of a jump box?
  Answer: Automation, Access Control, Security, Network Segmentation

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the data and system logs.
- What does Filebeat watch for?
  Answer: Filebeat monitors the log files that you choose, collects log events and sends them to Elasticsearch or Logstash for indexing.

- What does Metricbeat record?
  Answer: Metricbeat takes all the statistics and metrics it collects and sends them to the output that you choose like Elasticsearch or Logstash.

The configuration details of each machine may be found below.

| Name     | Function | IP Address  | Operating System |
|----------|----------|-------------|------------------|
| Jump Box | Gateway  | 10.0.0.6    | Linux            |
| Web1     | Webserver| 10.0.0.7    | Linux            |
| Web2     | Webserver| 10.0.0.8    | Linux            |
| Web3     | Webserver| 10.0.0.9    | Linux            |
| Elk      | ELK      | 10.1.0.4    | Linux            |
| LB       | LB       |13.93.207.73 | Linux            |
| Home     | Access C |73.76.146.159| Linux

### Access Policies

The machines on the internal network are not exposed to the public Internet.

Only the Elk Server machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
-73.76.146.159 through TCP 5601

Machines within the network can only be accessed by Home setup.
- JumpBox 10.0.0.6 via SSH port 22
- Home setup 73.76.146.159 via TCP port 5601_

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses  |
|----------|---------------------|-----------------------|
| Jump Box | No                  | 73.76.146.159         |
| Web1     | No                  | 10.0.0.6              |
| Web2     | No                  | 10.0.0.6              |
| Web3     | No                  | 10.0.0.6              |
| Elk      | No                  | 73.76.146.159 TCP 5601|
| LB       | No                  | 73.76.146.159 HTTP 80 |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- Ansible lets you easily and quickly deploy multiple tier apps by not needing to write custom code to automate your systems.


The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

Images/ElkDocker.png

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Web1 10.0.0.7
  Web2 10.0.0.8
  Web3 10.0.0.9

We have installed the following Beats on these machines:
- ElkServer, Web1, Web2, Web3

These Beats allow us to collect the following information from each machine:
- Filebeat: Logs Events
  Metricbeat: Metrics and system statistics

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned:

SSH into the control node and follow the steps below:
- Copy the '/etc/ansible/files/filebeat-config.yml' file to '/etc/filebeat/filebeat-playbook.yml'.
- Update the filebeat-playbook.yml file to include installer
- Run the playbook, and navigate to Kibana to check that the installation worked as expected.
