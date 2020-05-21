# Deployment_Nodejs
Full deployment of Node.js using PM2 and an NGINX reverse proxy and a free SSL from Lets Encrypt to a AWS EC2 instance

## What is Amazon EC2 Instance?
An EC2 instance is nothing but a virtual server in Amazon Web services terminology. It stands for **Elastic Compute Cloud**. It is a web service where an AWS subscriber can request and provision a compute server in AWS cloud.

---

## Create EC2 Instance in AWS

* Login to your AWS account and go to the AWS Services tab at the top left corner.
* Open all the services and click on EC2 under Compute services. This will launch the dashboard of EC2.
* On the top right corner of the EC2 dashboard, choose the AWS Region in which you want to provision the EC2 server.
* Click on 'Launch Instance' button in the section of Create Instance.
* Choose AMI(Amazon Machine Image)
* Choose EC2 Instance Types
* Configure Instance
* Add Storage
* Tag Instance
* Configure Security Groups
* Review Instances and select the key if it is existing if not create new key for your EC2 insance.
* Launch instance

---

## Connenct the EC2 instance Server ( Ubuntu using SSH ) 

* ``` chmod 400 <your pem key name> ```
* ```ssh -i <your pem key name> ubuntu@<Public DNS> OR ssh -i <your pem key name> ec2-user@<Public DNS>```

---
  
## Install Node JS

* ```sudo apt install curl```
* Then for the Latest release, add this PPA..
```curl -sL https://deb.nodesource.com/setup_10.x | sudo bash - ```
To install the LTS release, use this PPA
```curl -sL https://deb.nodesource.com/setup_8.x | sudo bash - ```
* ```sudo apt install nodejs```
* ```node -v```
*```npm -v```
---

## Install Git on Ubuntu

* ```sudo apt-get update```
* ```sudo apt-get install git```
* ```git --version```

---

## Clone the Repository

* ```git clone <Repository Path> ```

---



