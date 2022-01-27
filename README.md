# ELK-Stack-Project
Automated ELK Stack Deployment
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

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.
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

TODO: Which machine did you allow to access your ELK VM? What was its IP address?

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

TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc.
...
...

The following screenshot displays the result of running docker ps after successfully configuring the ELK instance.
Note: The following image link needs to be updated. Replace docker_ps_output.png with the name of your screenshot image file.


### Target Machines & Beats
This ELK server is configured to monitor the following machines:

TODO: List the IP addresses of the machines you are monitoring

We have installed the following Beats on these machines:

TODO: Specify which Beats you successfully installed

These Beats allow us to collect the following information from each machine:

TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., Winlogbeat collects Windows logs, which we use to track user logon events, etc.


### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned:
SSH into the control node and follow the steps below:

Copy the _____ file to _____.
Update the _____ file to include...
Run the playbook, and navigate to ____ to check that the installation worked as expected.

TODO: Answer the following questions to fill in the blanks:

Which file is the playbook? Where do you copy it?
Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?
_Which URL do you navigate to in order to check that the ELK server is running?

As a Bonus, provide the specific commands the user will need to run to download the playbook, update the files, etc.
