# project1-final
Anthony Valencia Cybersecurity Project !

## Automated ELK Stack Deployment
The files in this repository were used to configure the network depicted
below.
****[TODO: Update the path with the name of your
diagram](Images/diagram_filename.png)
These files have been tested and used to generate a live ELK deployment
on Azure. They can be used to either recreate the entire deployment
pictured above. Alternatively, select portions of the playbook.yml file may be
used to install only certain pieces of it, such as Filebeat.

****- _TODO: Enter the playbook file._
This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
- Beats in Use
- Machines Being Monitored
- How to Use the Ansible Build
### Description of the Topology
The main purpose of this network is to expose a load-balanced and
monitored instance of DVWA, the D*mn Vulnerable Web Application.
Load balancing ensures that the application will be highly efficient, in addition to restricting traffic to the network.
: This protects the servers from becoming overloaded, as well as protecting against Distributed Denial of Service (DDoS) attacks.
Integrating an ELK server allows users to easily monitor the vulnerable
VMs for changes to the logs and system metrics and statistics.
: Filebeat watches for any information that has been changed, and when the change took place.
: Metricbeat records metric and statistical data from the operating system and from services running on the server.
The configuration details of each machine may be found below.
_Note: Use the [Markdown Table
Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove
values from the table_.
| Name | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway | 10.0.0.1 | Linux |
| TODO | | | |
| TODO | | | |
| TODO | | | |
### Access Policies
The machines on the internal network are not exposed to the public
Internet.
Only the Jumpbox Provisioner machine can accept connections from the Internet. Access
to this machine is only allowed from the following IP addresses:
20.102.80.202
Machines within the network can only be accessed by SSH.
Which machine did you allow to access your ELK VM? What was its
IP address?_
20.102.80.202
A summary of the access policies in place can be found in the table
below.
| Name | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes/No | 10.0.0.1 10.0.0.2 |
| | | |
| | | |
### Elk Configuration
Ansible was used to automate configuration of the ELK machine. No
configuration was performed manually, which is advantageous because…
The main advantages of automating configuration through Ansible is the ease of use and an extremely easy learning curve. Through the use of Playbooks you are able to configure multiple Machines through the use of a single command after initial configuration.
The playbook implements the following tasks:
	Install docker.io
	Install python-pip
	Install docker container
	Launch docker container ELK
The following screenshot displays the result of running `docker ps` after
successfully configuring the ELK instance.
*****[TODO: Update the path with the name of your screenshot of docker ps
output](Images/docker_ps_output.png)
### Target Machines & Beats
This ELK server is configured to monitor the following machines:
 List the IP addresses of the machines you are monitoring_
(10.0.0.5, 10.0.0.7)
We have installed the following Beats on these machines:
	FileBeat
These Beats allow us to collect the following information from each
machine:
	Filebeat is a lightweight shipper for forwarding and centralizing log data. Filebeat monitors log files or locations you specify, collects log events, and forwards them either to Elasticsearch or Logstash for indexing.

Metricbeat collects metrics from the operating system and from services running on the server. Metricbeat then takes the metrics and statistics that it collects and ships them to the output that you specify.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control
node already configured. Assuming you have such a control node
provisioned:
SSH into the control node and follow the steps below:
- Copy the filebeat.yml and metricbeat.yml file to the /etc/ansible/roles/files/ directory.
- Update the configuration files to include the Private IP of the Elk-Server to the ElasticSearch and Kibana sections of the configuration file.
- Run the playbook, and navigate to ELK server to check that the installation
worked as expected.
: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_
The playbook is called filebeat-playbook.yml. You copy the file to the "/etc/ansible/hosts/" directory.
- _Which file do you update to make Ansible run the playbook on a
specific machine? How do I specify which machine to install the ELK
server on versus which to install Filebeat on?_
 The file you need to update is the filebeat.yml file which is a configuration file that will be dropped into the Elk-Server during the run of the ansible-playbook. When you update the host.cfg file in the ansible directory you will need to create a new group called [elkservers] and add the Private IP of the Elk-Server to the group. Then when configuring the filebeat.yml file you need to designate the Private IP of the Elk-Server in two lines of the .yml file. Lines 1106 and 1806 are the needed to be updated with the Private IP.

- _Which URL do you navigate to in order to check that the ELK server is
Running?
	http://[your.ELK-VM.External.IP]:5601/app/kibana
_As a **Bonus**, provide the specific commands the user will need to run
to download the playbook, update the files, etc._
-ssh RedAdmin@JumpBox(PrivateIP)
-sudo docker container list -a (locate your ansible container)
-sudo docker start container (name of the container)
-sudo docker attach container (name of the container)
-cd /etc/ansible/
-ansible-playbook elk.yml wait a couple minutes for the implementation of the Elk-Server
-cd /etc/ansible/roles/
-ansible-playbook filebeat-playbook.yml (installs Filebeat and Metricbeat)
-open a new web browser (Elk-Server PublicIP:5601) This will bring up the Kibana Web Portal
