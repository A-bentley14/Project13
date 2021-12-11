### Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![TODO: Update the path with the name of your diagram](Images/diagram_filename.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook file may be used to install only certain pieces of it, such as Filebeat.

  - _TODO: Enter the playbook file._   playbook file is separate

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
- _TODO: What aspect of security do load balancers protect? What is the advantage of a jump box?_ Load balancers protect the availability aspect. The Jump box gives you another layer of security and gives a place to host your containers

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the files and system metrics.
- _TODO: What does Filebeat watch for?_ Filebeat monitors log files to collect log events
- _TODO: What does Metricbeat record?_ Metricbeat records metrics from the server and OS

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.8   | Linux            |
| Web1     | Webserver| 10.0.0.6   | Linux            |
| Web2     | Webserver| 10.0.0.7   | Linux            |
| Web3     | Webserver| 10.0.0.9   | Linux            |
| Elk-serv | ELKserver| 10.1.0.5   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- _TODO: My personal Ip_

Machines within the network can only be accessed by the Jump Box at 10.0.0.8.
- _TODO: Which machine did you allow to access your ELK VM? What was its IP address?_ The Jumpbox at 10.0.0.8

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box |     No              | my public Ip         |
| ElkServer|  yes on port 5601   | the internet         |
|WebServers|     yes             | LB at 20.124.4.205   |
### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because it ensures that all the machines run the exact same thing
- _TODO: What is the main advantage of automating configuration with Ansible?_ allows every machine to be configured at once and all exactly the same 

The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- installs Docker
- installs python3
- installs docker python module
- increases memory to max
- launches the docker elk container after download

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.
 ![Docker_ps_output](https://user-images.githubusercontent.com/89419380/145687528-73d7ada6-a374-49b9-8afa-d7213816ae6e.PNG)



![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- _TODO: List the IP addresses of the machines you are monitoring_ 10.0.0.6  10.0.0.7   10.0.0.9

We have installed the following Beats on these machines:
- _TODO: Specify which Beats you successfully installed_
       filebeat and metricbeat
These Beats allow us to collect the following information from each machine:
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._ Filebeat logs changes to the files. Metricbeat logs all of the metric data.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the install-elk.yml file to ansible container folder.
- Update the hosts file to include the elk server ip address
- Run the playbook, and navigate to http://40.113.246.99:5601/app/kibana to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? elk-playbook.yml
 Where do you copy it?_ the ansible directory

- _Which file do you update to make Ansible run the playbook on a specific machine? the hosts file How do I specify which machine to install the ELK server on versus which to install Filebeat on?_ adding the private IP under servers

- _Which URL do you navigate to in order to check that the ELK server is running? 40.113.246.99:5601/app/kibana#

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
