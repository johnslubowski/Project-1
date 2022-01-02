# Project-1
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![TODO: Update the path with t![diagram]

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

  - _TODO: Enter the playbook file._

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
- : What aspect of security do load balancers protect?Load Balancing ensures availability to the web-servers  What is the advantage of a jump box?_
   The advantage of using a JumpBox is having the ease of administration of multiple systems'
   
Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the Logs and system metrics.
- Filebeat watches for log files/locations and collect log events. 
- Metricbeat records metrics and statistical data from services running on the server.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   | Linux            |
| Web-1    | WebServer| 10.0.0.7   | Linux            |
|          | Docker   |            |                  |
|          | DVWA     |            |                  |
| Web-2    | Webserver| 10.0.0.8   | Linux            |
|          | Docker   |            |                  |
|          | DVWA     |            |                  |
| ElkServer|Logserver | 10.1.0.4   |  Linux           |
                                
### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the jump box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
Personal IP Address

Machines within the network can only be accessed by SSH.
- The Elk Server is accessible by SSH from JumpBox from web access from Personal IP Address.

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | No                  | Personal IP Address  |
| Web 1    |Yes Thru LoadBalance |  10.0.0.7            |
| Web 2    |Yes Thru LoadBalancer|  10.0.0.8            |
|ElkServer | No                  | Personal

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- By automating the installation servers can be deployed quickly,and updates can become faster.

The playbook implements the following tasks:
- Install Docker io and pip3 
- Increase VM Memory
- Download and Configure Elk docker container  

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Web-1 (10.0.0.7)
- Web-2 (10.0.0.8)

We have installed the following Beats on these machines:
- Filebeat
- Metricbeat

These Beats allow us to collect the following information from each machine:
-Filebeat is a shipper for centralizing log data.it monitors log files,collects log events, forwards them to Elasticsearch or Logstash.
-Metricbeat will collect metrics and statistics sending the info to Elasticsearch or Logstash. 

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the filebeat-config.yml and metricbeat-config,yml file to /etc/ansible/hosts
- Update the configuration files to include IP address of the Elk Server VM and webservers.
- Run the playbook, and navigate to  http://[Elk_VM_Public_IP]:5601/app/kibana to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_
- 
- Elk-playbook.yml- used to install Elk server
          

          
 _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
- _Which URL do you navigate 

Filebeat-playbook.yml-used for installing and cofig Filebeat on Elk server and DVWA
          
to in order to check that the ELK server is running?

 Metricbeat-playbook.yml- used for installing Mertricbeat on the Elk server and DVWA
          
_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
