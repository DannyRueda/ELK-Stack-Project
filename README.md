# ELK-Stack-Project
### Automated ELK Stack Deployment
The files in this repository were used to configure the network depicted below.

![Cloud Network](https://user-images.githubusercontent.com/56982183/151463107-2f33b421-e86a-4221-9799-ce64c1d20824.png)


These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook/yaml file may be used to install only certain pieces of it, such as Filebeat.

The following playbook/yaml files were created and used to generate the live ELK enviornment on Azure: 

-  [DVWA (Act1.yml)](
https://github.com/DannyRueda/ELK-Stack-Project/blob/main/Ansible/Act1.yml)
-  [ELK install (ELK-startup.yml)](https://github.com/DannyRueda/ELK-Stack-Project/blob/main/Ansible/ELK-startup.yml)
-  [Filebeat (filebeat-playbook.yml)](https://github.com/DannyRueda/ELK-Stack-Project/blob/main/Ansible/filebeat-playbook.yml)
-  [Metricbeat (metricbeat-playbook.yml)](
https://github.com/DannyRueda/ELK-Stack-Project/blob/main/Ansible/filebeat-playbook.yml)

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the Dang Vulnerable Web Application.
Load balancing ensures that the application will be highly available, in addition to restricting access to the network.

- Load balancers are used to typically prevent and protect the availablility aspect of the CIA Traid. The reason is that they can protect against DDos (distributed denial-of-service) attacks. The advantage of a load balancer is that it is connected to various servers. This means that if one server is down or disfunctional the load balancer can direct traffic to another server.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the data and system logs.

- Filebeat uses one single command to parse, collect, and visualize ELK logs. This is important because when taking raw logs and trying to understand them can be difficult and time consuming.
- Metricbeat is used to collect metric data from both operating systems and services that are running on a server. Instead of having to collect and export the data yourself from the server to Elasticsearch or Logstash, metricbeat does it for you.

The configuration details of each machine may be found below.


| Name     | Function | IP Address     | Operating Systems |
|----------|----------|----------------|-------------------|
| Jump Box | Gateway  | 20.124.106.225 | Linux             |
| Web-1    | Server   | 10.0.0.5       | Linux             |
| Web-2    | Server   | 10.0.0.6       | Linux             |
| ELK-VM   | Server   | 10.1.0.4       | Linux             |







### Access Policies
The machines on the internal network are not exposed to the public Internet.
Only the Jump Box provisioner machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:

- 20.124.106.225

Machines within the network can only be accessed by an ansible container in the Jump Box provisioner.


Jump Box Provisioner:
- Public IP: 20.124.106.225
- Private IP: 10.1.0.4

A summary of the access policies in place can be found in the table below.


| Name       | Publicly Accessible     | Allowed IP Addresses |
|------------|-------------------------|----------------------|
| Jump Box   | No (SSH - Port 22, TCP) | 98.32.92.242         |
| Web-1      | No (SSH - Port 22, TCP) | 98.32.92.242, 10.0.0.4|
| Web-2      | No (SSH - Port 22, TCP) | 98.32.92.242, 10.0.0.4|
| ELK VM     | No (SSH - Port 22, TCP) | 98.32.92.242, 10.0.0.4|


### Elk Configuration
Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because you can configure other virtual machines without needing to enter into them. This automation can also save up time by decreasing the chance of human error while trying to configure a machine manually.

The playbook implements the following tasks:

 - Install Docker: allows docker to insall in the server, which is accessible to other servers.
 - Python3-pip: allows a package-management system to install and manage software package in the server.
 - Install Docker Module: allows the installation of docker components.
 - Increase Memory: tells the docker container to increase the memory, allows more resources.
 - Use more Memory: tells the docker container to use more memory, allows a smoother launch.
 - Download/Launch Elk Container: allows the installation of the ELK docker container and the starts it with the specified paramiters attached to the playbook.
 - Enable service docker on boot: Everytime the system reboots the service docker is still running.

The following screenshot displays the result of running docker ps after successfully configuring the ELK instance.
![docker_ps_output](https://user-images.githubusercontent.com/56982183/154605066-f1c597dc-ae0e-48c6-aa11-bdfc16d17656.jpg)



### Target Machines & Beats
This ELK server is configured to monitor the following machines:

 - 10.0.0.5 (Web 1)
 - 10.0.0.6 (Web 2)

We have installed the following Beats on these machines:

 - Filebeat
 - Metricbeat

These Beats allow us to collect the following information from each machine:

 - Filebeat is used to monitor log files that the user specifies. We specified it to collect logins, which allows us to see who is logging into the system.

 - Metricbeat is used to collect statistics and metrics. We collected memory, cpu, and other useful information which would help us what programs are taking up the systems resources.


### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned:
SSH into the control node and follow the steps below:

Copy the ELK-startup.yml file to /etc/ansible/playbooks/ELK-startup.yml.
Update the hosts file to include the ELK server by including the destination IP address.
Run the playbook, and navigate to https://10.1.0.4:5601/app/kibana to check that the installation worked as expected.
