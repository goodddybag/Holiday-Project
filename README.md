# HOLIDAY PROJECT


## Task

Set up 2 EC2 instances on AWS(use the free tier instances).
Deploy an Nginx web server on these instances(you are free to use Ansible)
Set up an ALB(Application Load balancer) to route requests to your EC2 instances
Make sure that each server displays its own Hostname or IP address. You can use any programming language of your choice to display this.


## Instruction

I should not be able to access your web servers through their respective IP addresses. Access must be only via the load balancer
You should define a logical network on the cloud for your servers.
Your EC2 instances must be launched in a private network.
Your Instances should not be assigned public IP addresses.
You may or may not set up auto scaling(I advice you do for knowledge sake)
You must submit a custom domain name(from a domain provider e.g. Route53) or the ALB’s domain name.

### Solution

I used Cloud Formation to automate this project

I created two files which is a newtwork file and server file

Network file was used to create my vpc which contains a pair of public and private subnet, each contains NAT gateway. I also created aroute tables.This stack, after created successfully, it output some global values such as the id of the VPCs and Subnets can can be used by another stack. 

The server file contains script to automate the creation of servers in the private subnets. The servers are created as part of an Autoscaling group with one instance in each of the private subnets. The instances can only cummunicate with the internet using the NAT gateway. Created a load balancer that helps in taking requests from users back tto the private instance

I created a Network Parameters File which contains the parameter variables for the network file. In this file, you have to state the cidr block you want the network to use. 

I created a server parameter file which contains the parameter variables for the server file

I Created a Stack file which helps to run the aws cloud formation command to create a stack. You run it in this manner



