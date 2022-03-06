## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

[Personal diagram](https://user-images.githubusercontent.com/100634576/156908477-90ee744c-82bd-412f-ac57-af6eeba359cc.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the <b>YAML</b> file may be used to install only certain pieces of it, such as Filebeat.

  [ELK-playbook.txt](https://github.com/DVega814/Cybersecurity/files/8191988/ELK-playbook.txt)

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly avaiable, in addition to restricting restricting to the network.
<br> What aspect of security do load balancers protect? <b> Load balancers defend against denial of service</b> <br>
What is the advantage of a jump box? <b> The advantage of a jump box is that all admins first connect to before launching any administrative task or use as an origination point to connect to other servers or untrusted environments </b>

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the <b> Data </b> and system <b> Logs </b>. <br>
<br> What does Filebeat watch for? <b> Filebeat is a lightweight shipper for forwarding and centralizing log data </b><br>
<br> What does Metricbeat record? <b> Metricbeat takes the metrics and statistics that it collects and ships them to the output that you specify, such as Elasticsearch or Logstash. </b><br>

The configuration details of each machine may be found below.

| Name     | Function   | IP Address | Operating System |
|----------|------------|------------|------------------|
| Jump Box | Gateway    | 10.0.0.4   | Linux            |
| Web 1    | Webserver  | 10.0.0.5   | Linux            |
| Web 2    | Webserver  | 10.0.0.6   | Linux            |
| ELK-VM   | ELK server | 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the <b> JumpBox</b> machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses: <b> My Public IP </b>

Machines within the network can only be accessed by <b> JumpBox </b>.
Which machine did you allow to access your ELK VM? What was its IP address? <b> JumpBox </b> <I><b> IP Address: 10.0.0.4</I></b> 

A summary of the access policies in place can be found in the table below.

| Name       | Publicly Accessible | Allowed IP Addresses |
|------------|---------------------|----------------------|
| JumpBox    | Yes/No              | My Public IP         |
| ELK-Server | Yes (Port 5601)     | 20.114.190.231       |
| Web 1      | No                  | 20.124.131.176       |
| Web 2      | No                  | 20.124.131.176       |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because <b> servcies running can be limited, system installation and update can be streamlined, and processes become more replicable</b> <br>
-What is the main advantage of automating configuration with Ansible? <b> The main advantage of automating configuration with Ansible is that it's very simple to set up and use and No special coding skills are necessary to use Ansible's playbooks. </b> <br>

The playbook implements the following tasks:
- <b> Installs docker.io </b>
- <b> Installs python3-pip </b>
- <b> Installs docker, which is the Docker Python pip module. </b>
- <b> Increase Virtual Memory </b>

The following screenshot displays the result of running `docker ps` ('sudo docker container list -a') after successfully configuring the ELK instance.

![elk docker](https://user-images.githubusercontent.com/100634576/156909866-bc9f8c9d-3bf4-4e01-8410-40f1fc6ceadc.PNG)


### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Web 1 - 10.0.0.5
- Web 2 - 10.0.0.6

We have installed the following Beats on these machines:
- Filebeat
- Metricbeat

These Beats allow us to collect the following information from each machine:<br>
- <b> Filebeat- collects data about the file system</b> <br>
- <b> Metricbeat- collects machine metrics</b>

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the <b>playbooks</b> file to <b>/etc/ansible.</b>
- Update the <b>ansible</b> file to include <b> a files and roles directory</b>
- Run the playbook, and navigate to <b> or ssh into each VM (Web 1 & Web 2) check that the installation worked as expected. </b>

- Which file is the playbook? <br>
 <br> [filebeat-playbook.yml.txt](https://github.com/DVega814/Cybersecurity/files/8192006/filebeat-playbook.yml.txt)
 <br> [metricbeat-playbook.yml.txt](https://github.com/DVega814/Cybersecurity/files/8192007/metricbeat-playbook.yml.txt) <br>
- Where do you copy it? <b>Both playbooks were copied to the roles directory within /etc/ansible </b>


- Which file do you update to make Ansible run the playbook on a specific machine?  How do I specify which machine to install the ELK server on versus which to install Filebeat on? <br> <b> cd into /etc/ansible/ then nano into hosts from there edit webservers to include Web 1 and Web 2 </b>

![aansible_hosts](https://user-images.githubusercontent.com/100634576/156911131-dc9843d3-c156-4e78-817a-5a9b1dc22b6d.PNG)

- Which URL do you navigate to in order to check that the ELK server is running? <b> http://20.114.190.231:5601 </b>
