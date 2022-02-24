# Project-1-Web-stack-implementation-on-aws

#### This project will demonstrate how a LAMP stack is implemented on an AWS EC2 virtual server.

### Introduction

Solution stacks are sets of individual components that create a complete environment for application development. The components are usually independently developed, but their frequent combined usage and compatibility qualify them to become a stack. For example, developers need an operating system, a web server, database management software, and a programming language to create a web application. 

LAMP consists of four components necessary to establish a fully functional web development environment. The first letters of the components' names make up the LAMP acronym:

   •	Linux is a free and open-source operating system used to run the rest of the components. Linux is popular in part because it offers more flexibility and configuration options than some other operating systems.
   •	Apache HTTP Server is a web server software used to serve static web pages.

   •	MySQL is a relational database management system used for creating and managing web databases, but also for data warehousing, application logging, e-commerce, etc.

   •	PHP is an open-source scripting language works with Apache to help you create dynamic web pages. You cannot use HTML to perform dynamic processes such as pulling data out of a database. To provide this type of functionality, you simply drop PHP code into the parts of a page that you want to be dynamic. 

This project will give you a better understanding of what the LAMP stack is and how to implement your LAMP stack on Amazon Web Services (AWS). AWS is the biggest Cloud service provider, and it offers a free tier account that we will be able to utilize for our project. For the purpose of this specific project, we will be employing [EC2 (Elastic Compute Cloud) service](https://aws.amazon.com/ec2/?nc2=h_ql_prod_cp_ec2).

### Setting up our Virtual Environment

In order to complete this project, we need to begin by setting up an AWS account and a virtual server with Ubuntu Server OS. 

Step 1:  
Create free AWS account. Instructions for this can be found [here](https://aws.amazon.com/premiumsupport/knowledge-center/create-and-activate-aws-account/). Once you have created your AWS account, navigate to the login page and type in your credentials.
![step1](https://user-images.githubusercontent.com/91766546/155464784-d05cdd49-bd8e-44cd-a7f2-375be234f08c.png)

Step 2: 
After signing-in to your AWS account, navigate to the top-right corner of your screen and select your preferred region. This should be the closest region to your physical location.
![step2](https://user-images.githubusercontent.com/91766546/155465696-7db8eb54-0b61-4650-ba9b-1d72fbe6a2a3.png)

Step 3:
Proceed to the search bar and type in EC2. Select the EC2 service that appears on top.
![step3](https://user-images.githubusercontent.com/91766546/155465963-bc4692d7-dd76-4671-8bf5-539ec429df81.png)

Step 4:
Click on the orange 'Launch Instances' button that appeears on the top right side of your screen.
![step4](https://user-images.githubusercontent.com/91766546/155466281-6f017c25-a13b-4ed7-ab75-359fe66e4a28.png)

Step 5:
Choose the Ubuntu Server 20.04 LTS (HVM) as the Amazon Machine Image (AMI) from the list of AMIs provided. 
![step5](https://user-images.githubusercontent.com/91766546/155466520-587e7761-c42e-4e69-944e-17889cb7e67e.png)

Step 6:
Select t2.micro as the instance type
![step6](https://user-images.githubusercontent.com/91766546/155466629-4cb51271-8c9f-4d8f-bab1-5b1122854e55.png)
click REVIEW AND LAUNCH.

Step 7:
and then on the next page choose LAUNCH.
![step7](https://user-images.githubusercontent.com/91766546/155466863-53cbbfff-96ac-4ce4-beb3-d252ebefeb4b.png)

Step 8:
There will be a window asking you to create a key pair. Select the 'Create a new key pair' option from the drop down menu and then select "Download". Make sure you know the location the file was downloaded to and don't lose the .pem file. You will need this file in order to connect into your server from your local PC. After you downloaded the key pair, check the box for the acknowledgement, and then click on "Launch Instances".
![step8](https://user-images.githubusercontent.com/91766546/155467313-064c49ff-925a-4981-8f65-2fc18bae114a.png)

Step 9:
Woohoo!!! You've successfully launched an EC2 instance! 
![step9](https://user-images.githubusercontent.com/91766546/155467506-76e1fe69-e888-4394-bdab-b12cb3fd675a.png)

Step 10:
Click on 'View Instances' to see your EC2 instance.
![step10](https://user-images.githubusercontent.com/91766546/155467923-c75aee26-436b-4b91-be39-6e41e0ae17f7.png)

### Let's connect our AWS EC2 server to your local PC via SSH

Step 1:
On your local Linux machine, change your working directory to the location where your downloaded key pair .pem file exists. 
And use the 'ls' command to check if the file exists in that folder.
![step11](https://user-images.githubusercontent.com/91766546/155468644-c2e6e376-61fa-4404-b22b-36f1e420a321.png)

Step 2:
Use the following commang to change the premissions for the private key file (.pem), otherwise you can get an error 'Bad permissions'.
![step12](https://user-images.githubusercontent.com/91766546/155468937-57c37275-ca8e-41ef-a7d2-4d7976d24938.png)

Step 3:
Get your public IP address from your instance
![step13](https://user-images.githubusercontent.com/91766546/155469264-77680e47-94ff-4aa5-9ea2-4aca85ffee4f.png)

Step 4:
Connect to your EC2 instance by running the following command.
![step14](https://user-images.githubusercontent.com/91766546/155469328-97582ec5-b365-4e73-afd5-cd2cad9640ae.png)
![step15](https://user-images.githubusercontent.com/91766546/155469524-b58b041b-3366-4eaf-9adf-cb99633c29b5.png)

When connected, your ip-address will be shown on your terminal.
![step16](https://user-images.githubusercontent.com/91766546/155469556-bdb0ba33-ef4c-4dc7-915e-2295bdae648a.png)

## Installing Apache 

##### What is Apache?

Apache is a popular open-source, cross-platform web server that is, by the numbers, the most popular web server in existence. One of the pros of Apache is its ability to handle large amounts of traffic with minimal configuration. It scales with ease and with its modular functionality at its core, you can configure Apache to do what you want, how you want it. You can also remove unwanted modules to make Apache more lightweight and efficient.

Let's proceed with our installation

Step 1:
On your terminal, update a list of packages in package manager using the following command.
![step17](https://user-images.githubusercontent.com/91766546/155471051-08cc3dce-b4a3-493f-9c1a-b79683d552ec.png)

Step 2:
Run apache2 package installation command. Click Y for Yes when the prompt appears.
![step18](https://user-images.githubusercontent.com/91766546/155471117-fa89e28a-47f2-4f1d-8724-ec8a77199f45.png)
![step19](https://user-images.githubusercontent.com/91766546/155471319-4f1fe8c6-cae6-49e3-8d42-4fc575d48078.png)

Step 3:
To verify that apache2 is running as a Service in our Operating System, use following command.
![step20](https://user-images.githubusercontent.com/91766546/155471425-c3dfbaff-f9ac-4ce4-82fe-9132fc37b2ba.png)
If it is green and running, then you did everything correctly. Congratulations!!! You have just launched your first Web Server in the Clouds!

Step 4:
Before we can receive any traffic by our Web Server, we need to open TCP port 80 which is the default port that web browsers use to access web pages on the Internet. We have TCP port 22 open by default on our EC2 machine to access it via SSH, so we need to add a rule to EC2 configuration to open inbound connection through port 80:

Open your AWS Management Console and Click on your EC2 instance. Click on the 'Security' tab.
![step21](https://user-images.githubusercontent.com/91766546/155471913-65b8e592-f91c-4085-8d09-f410b8694a2b.png)

Click on the link under the 'Securty Groups'.
![step22](https://user-images.githubusercontent.com/91766546/155472624-d79fdc64-6ec9-467d-bf57-33ebc2687c23.png)
















