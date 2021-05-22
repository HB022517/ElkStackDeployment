## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

<img src="/DIagrams/ELKDEPLOYDiagram.jpg"/>


These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the filebeat-playbook.yml file may be used to install only certain pieces of it, such as Filebeat.

  - _TODO: Enter the playbook file._

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly Available, in addition to restricting access to the network.
- _TODO: What aspect of security do load balancers protect? What is the advantage of a jump box?_
     The Docker containers for DVWA, Filebeat and Metricbeat are placed behind Load Balencers, because they allow access to not regularly accessable WebVM's that carry that pertinent information. The Load Balancer distributes the loads across the machines in an effort to be proactive against any single-point machine failure.
     
     The advantage of a JumpBox is that in short its explicity restrictive in regards to whom can acces the network. You have to SSH into the JumpBox in order to ingress into docker containers and move to any other machines that may be on the network. They afford a single port of entry therby making it easier to monitor and allow for implementation of intricate security procedures which can assist with the hardening of the entire network
     
     
Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the Network and system Files.
- _TODO: What does Filebeat watch for?
- Filebeat monitors log data, events, and files, then forwards them to Elastisearch or Logstash to be indexed.
- 
- _TODO: What does Metricbeat record?_
- Metricbeat collects differnt metrics from the OS and services running on the server.
- 
- The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

![image](https://user-images.githubusercontent.com/41927632/119171132-2792df00-ba32-11eb-8f99-3ef26806625f.png)



### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the JumpBox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 71.204.51.244

It also bears mentioning that a change to the firewall rule is a msust to allow traffic only from the Public IP of the entity it represents. With that said, 71.204.51.244 has to be used to move forward.

Machines within the network can only be accessed by The JumpBox's address.
- _TODO: Which machine did you allow to access your ELK VM? What was its IP address?_

A summary of the access policies in place can be found in the table below.

![image](https://user-images.githubusercontent.com/41927632/119175420-cff77200-ba37-11eb-8ce0-d3fbf7295e97.png)


### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- _TODO: What is the main advantage of automating configuration with Ansible? Some would say that Ansible allows IT administrators to automate away the laborious drudgery from their daily duties, therby freeing them up to focus on more important tasks. Ulitimaltely, Ansible is ffree and an open source tool, and because of its power allows you to model even the most highly complex IT workflow.

The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._

•	Install Docker.io
•	Install pip3 in addition to the Python Docker Module
•	Allows an increase in Virtual Memory
•	Ensures that ELK runs every time the machine is booted 
•	Downloads and launches a docker ELK container with the following published ports: 5601 9200 5044

- ...

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output] 
![SharedScreenshotBash](https://user-images.githubusercontent.com/41927632/119177727-b99ee580-ba3a-11eb-9cbe-ecf2649c793a.jpg)


### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- _TODO: List the IP addresses of the machines you are monitoring
  Webservers with Internal IP's 10.2.0.5. 10.2.0.6 10.2.0.7

We have installed the following Beats on these machines:
- _TODO: Specify which Beats you successfully installed_ We successfully installed Filebeat and Metricbeat.
•	Filebeat monitors traffic by collecting log data on devices.
•	Metricbeat collects data from OS, CPU or Memory any data about anything on running on the server.


These Beats allow us to collect the following information from each machine:
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the Deployment file to /etc/ansible/roles.
- Update the /etc/ansible/hosts to include remote_user=AZADMIN the user name for each VM.
- Update the /etc/ansible/hosts file to include the IP address in the webservers & ELK groups. it is paramount to uncomment the webservers selection and add the ELK section so it will work
- Run the playbook, and navigate to http://40.76.213.190:5601/app/kibana to make sure the install worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
/etc/ansible/elk-playbook.yml should be copied to your directory.

The hosts file should be updated to make Ansible run the playbook on a specific machine. How do I specify which machine to install the ELK server on versus which to install Filebeat on? Just add the private IP under "servers"
- _Which URL do you navigate to in order to check that the ELK server is running?
- http://40.76.213.190:5601/app/kibana
- 

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
