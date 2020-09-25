## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![Network diagram map](https://github.com/BrenaBaby/Project1/blob/master/Project/Images/Project%20map%20(1).png)      

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the Filebeat_Metricbeat_setup.yml file may be used to install only certain pieces of it, such as Filebeat.

[Elk_deployment.yml](https://github.com/BenjaminBartholomew/Automated_ELK_Stack/blob/master/Ansible_YML_Scripts/install-elk.yml)

[Filebeat_Metricbeat_setup.yml](https://github.com/BrenaBaby/Project1/blob/master/Project/YML%20files/Filebeat_Metricbeat_setup.yml)

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly redundant, in addition to restricting access to the network.
- _TODO: What aspect of security do load balancers protect? What is the advantage of a jump box?_

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system metrics.
- Filebeat monitors logs and files on the chosen machines.
- Metricbeat monitors systems and services on the chosen machines, such as CPU and memory.

The configuration details of each machine may be found below.

| Name               | Function       | IP Address | Operating System |
|--------------------|----------------|------------|------------------|
| JumpBoxProvisioner | Gateway        | 10.0.0.4   | Linux Ubuntu 18  |
| Web-1              | DVWA container | 10.0.0.5   | Linux Ubuntu 18  |
| Web-2              | DVWA Container | 10.0.0.6   | Linux Ubuntu 18  |
| Web-3              | DVWA Container | 10.0.0.7   | Linux Ubuntu 18  |
| Venison            | ELK Container  | 10.1.0.4   | Linux Ubuntu 18  |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the JumpBoxProvisioner machine can accept connections from the Internet. Access to this machine is only allowed from the following IP address:

- 98.224.101.148

Machines within the network can only be accessed by the JumpBoxProvisioner machine with the IP address of:
- 10.0.0.4

A summary of the access policies in place can be found in the table below.

| Name               | Publicly Accessible | Allowed IP Addresses         |
|--------------------|---------------------|------------------------------|
| JumpBoxProvisioner | Yes                 | 98.224.101.148               |
| Web-1              | No                  | 10.0.0.4                     |
| Web-2              | No                  | 10.0.0.4                     |
| Web-3              | No                  | 10.0.0.4                     |
| Venison            | Yes                 | 98.224.101.148 10.0.0.4      |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because you don't have to run each one individually and can be run on multiple machines at once.

The playbook implements the following tasks:
- Installs Docker on the machine
- Installs python
- Installs the python module to docker
- Increases the amount of memory to be used on the machine
- Sets the machine to use the new increased size of memory
- Downloads and launches a docker Elk container with the published ports of 5601, 9200, and 5044.

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![Docker PS](https://github.com/BrenaBaby/Project1/blob/master/Project/Images/Elk%20Container.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Web-1: 10.0.0.5
- Web-2: 10.0.0.6
- Web-3: 10.0.0.7

We have installed the following Beats on these machines:
- Filebeat
- Metricbeat

These Beats allow us to collect the following information from each machine:
- Filebeat collects logs and files which Metricbeat collects system and service information. Both Filebeat and Metricbeat collect information and displays it in an easy way to analyze and monitor.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the Elk_deployment.yml file to ~/etc/ansible/.
- Update the Elk_deployment.yml file to include the appropriate host group from the ~/etc/ansible/hosts file.
- Run the playbook, and navigate to http://[elk server public IP]:5601/app/kibana#/home to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
- URL for Kibana: http://40.69.160.141:5601/app/kibana#/home
