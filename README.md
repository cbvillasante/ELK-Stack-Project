# ELK-Stack-Proyect
Configuration of  an ELK stack server in order to set up a cloud monitoring system

Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![ELK DIAGRAM](https://user-images.githubusercontent.com/101161631/159064627-71c8c2d1-1f6e-40d1-aa3b-586961ae6952.png)


This document contains the following details:

    •	Description of the Topology

    •	Access Policies

    •	ELK Configuration

        -Beats in Use
    
        -Machines Being Monitored

    •	How to Use the Ansible Build

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application. Load balancing ensures that the application will be highly available , in addition to restricting access to the network.


What aspect of security do load balancers protect? 

    The process of distributing the traffic efficiency across the network is monitored by the Load Balancer, which plays an important role in mitigating    denial of service attacks (DDoS). Another of its important functions is to check regularly to make sure the machine behind the load balancer is       functioning before sending traffic to them, if there is a problem with any machine, the load balancer starts sending traffic to another machine to avoid overloading. (Fault tolerance). This distribution improves application responsiveness and increases the availability of applications and websites to users.


What is the advantage of a jump box?

    The advantage of the jump box is that it is a secure computer that all administrators connect to first as a test mode before connecting to other untrusted servers or environments and prevents all the Virtual machines to be exposed to the public.


What does Filebeat watch for?


    Filebeat is part of the ELK stack and monitors the log files or locations that you specify, collects log events and data .  


What does Metricbeat record?

    Metricbeat collect metric data from your target servers, operating system metrics  such as CPU or memory or data related to services running on the server. It can also be used to monitor other beats and ELK stack itself. 


The configuration details of each machine may be found below.

    NAME.             FUNCTION.                         IP ADDRESS.             OPERATING SYSTEM

    Jump BoX.         Gateway/Ansible.                  10.0.0.4.               Linux Ubuntu 

    Web-1.            Web server to run DVWA            10.0.0.5.               Linux Ubuntu 

    Web-2.            Web server to run DVWA            10.0.0.6.               Linux Ubuntu

    Elk.              Run Elk Container and Kibana      10.1.0.4.               Linux Ubuntu 


Access Policies

    The machines on the internal network are not exposed to the public Internet.
    Only the Jump Box Provisioner  machine can accept connections from the Internet. 
    Access to this machine is only allowed from the following IP addresses: 68.201.131.45.
    Machines within the network can only be accessed by Jump-Box Provisioner.


Which machine did you allow to access your ELK VM? What was its IP address?

    We allowed Jump box ip address 20.127.37.77   

A summary of the access policies in place can be found in the table below:

    Name	             Public Accessible	       Allowed IP Address
    Jump Box	     Yes via Port 22	         68.201.131.45
    Web-1	             No	                         10.0.0.4
    Web-2	             No	                         10.0.0.4
    ELK	             Yes via port 5601	         68.201.131.45
    Load Balancer	     Yes via port 80	         68.201.131.45


Elk Configuration

    Ansible was used to automate the configuration of the ELK machine. No configuration was done manually, which is advantageous because it helps us configure multiple machines which makes the process easier and minimizes human error.

 
The playbook implements the following tasks:

    .Specify the name of the configuration and the remote user.

    .Docker.io installation.

    .Python3-pip installation.

    .Docker Module Installation.

    .Increase Virtual Memory by using sysctl.

    .Download and launch a docker elk container with exposed ports.

    .Enable service docker on the boot.


The following screenshot displays the result of running docker ps after successfully configuring the ELK instance.



Target Machines & Beats

    This ELK server is configured to monitor the following machines:

    WEB-1 10.0.0.5

    WEB-2 10.0.0.6

    We have installed the following Beats on these machines:

    •	Filebeat

    •	Metricbeat


These Beats allow us to collect the following information from each machine:

Filebeat helps to organize and generate log files from specific files such as Apache ,Microsoft Azure ,The Nginx web server and MySQL databases. Metricbeat collects all metrics  information from the operation system and services that are running on the server  such as CPU or memory used.


Using the Playbook

     In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned:
     SSH into the control node and follow the steps below:

    •	Copy the configuration file and the playbook to etc/ansible.

    •	Update the hosts file to include the private IP address of the machine we want to install ELK in (10.1.0.4).

    •	Run the playbook and navigate to Kibana(elkipublic_ip:5601) to check that the installation worked as expected.


Which file is the playbook? Where do you copy it?

    The YAML is the playbook file which must be copied into the /etc/ansible directory in the Ansible container.


Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?
     
     The hosts file in the etc/ansible directory must be updated. We should add the vm private ip under [ELKS] (10.1.0.4).
     
Which URL do you navigate to in order to check that the ELK server is running?

    In my infrastructure this is the URL  http://52.190.136.59:5601/ 
    
     
![Kibana](https://user-images.githubusercontent.com/101161631/159068666-8b02bdfc-2949-421a-a1a5-63056f5d3b8b.png)

























