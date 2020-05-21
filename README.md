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

# Test Application

* test your application, run <app starting js file name> with the following command:
  
``` node <app starting js file name> or npm start ```

* Once you have confirmed the application is working, kill the application with CTRL+C.

# Install & Configure PM2

* ```
sudo npm install -g pm2```
* ```sudo pm2 start /path/<your application starting file name where you defining your port> default app it should be sudo pm2 start /application path/./bin/www ```
* check using 
``` <your puplic ip>:<your application port>``` in your browser. your application is running.


# Install nginx

Since this is our first interaction with the apt packaging system in this session, we will update our local package index so that we have access to the most recent package listings.

* 
```
sudo apt-get update ```

* ```
sudo apt-get install nginx
```
* check in your browser enter <your puplic ip> you will get Welcome to nginx screen


# Set Up Nginx as a Reverse Proxy

Now that your application is running and listening on localhost, you need to make it so people from the outside world can access it. To achieve this, we will use Nginx as a reverse proxy.
* First, you need to update the ```/etc/nginx/sites-available/default``` configuration file. 
Open the file with this command:
``` cd /etc/nginx/sites-available ```
```sudo vi default```
 
**OR**
* instead of this you can also use nano command for open your configuration file: 

```  sudo nano /etc/nginx/sites-available/default```


* Within the server block, find the location / section. Replace the contents of the block with the following configuration:


```
location / {
proxy_pass http://localhost:**<your port number>**;
proxy_http_version 1.1;
proxy_set_header Upgrade $http_upgrade;
proxy_set_header Connection 'upgrade';
proxy_set_header Host $host;
proxy_cache_bypass $http_upgrade;
}
```
