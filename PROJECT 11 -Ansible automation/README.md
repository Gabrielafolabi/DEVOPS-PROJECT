## ANSIBLE AUTOMATE PROJECT

![Alt text](image.png)

On the diagram above, the virtual private Network (VPC) is divided into teo subnets - public subnet and private subnet. The private subnet is only reachabale by private IP addresses. The public subnet has public ip addresses.

A jump server in the above( Sometimes refered to as Bastion Host) is an intermediary server through which access to internal network can be provided. according to this diagram above, the web servers are inside a secure network which cannot be reached directly from the internet. That means, even DevOps engineers cannot ssh into the webservers directly and can only access it through a jump server- it provides better security and reduce attack surface.

In this project, I will developed `Ansible` scripts to simulate the use of a `jump box/Bastion host` to access Web servers.

## Install and configure Ansible Client to act as a Jump Server/Bastion Host