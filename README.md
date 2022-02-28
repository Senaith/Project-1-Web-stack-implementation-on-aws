# Project-1-Web-stack-implementation-on-AWS

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
Click on the orange 'Launch Instances' button that appears on the top right side of your screen.

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
You've successfully launched an EC2 instance! 

![step9](https://user-images.githubusercontent.com/91766546/155467506-76e1fe69-e888-4394-bdab-b12cb3fd675a.png)

Click on 'View Instances' to see your EC2 instance.

![step10](https://user-images.githubusercontent.com/91766546/155467923-c75aee26-436b-4b91-be39-6e41e0ae17f7.png)

### Let's connect our AWS EC2 server to your local PC via SSH

Step 1:
On your local Linux machine, change your working directory to the location where your downloaded key pair .pem file exists. 
And use the 'ls' command to check if the file exists in that folder.

![step11](https://user-images.githubusercontent.com/91766546/155468644-c2e6e376-61fa-4404-b22b-36f1e420a321.png)

Step 2:
Use the following command to change the permissions for the private key file (.pem), otherwise you can get an error 'Bad permissions'.

![step12](https://user-images.githubusercontent.com/91766546/155468937-57c37275-ca8e-41ef-a7d2-4d7976d24938.png)

Step 3:
Get your public IP address from your instance.

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

Step 5: 
Click on the link under the 'Security Groups'.

![step22](https://user-images.githubusercontent.com/91766546/155472624-d79fdc64-6ec9-467d-bf57-33ebc2687c23.png)


Step 6:
Next, click on 'Edit Inbound Rules' box found on the bottom right side of your screen.

![step23](https://user-images.githubusercontent.com/91766546/155531100-3456c502-5c34-4f6f-b132-3a1751834863.png)

Step 7:
Click on 'Add Rule' and add the HTTP, TCP port 80 and allow source from anywhere by using 0.0.0.0

![step24](https://user-images.githubusercontent.com/91766546/155531343-2e16c23f-6389-45e8-b2a1-e75435314d51.png)

![step25](https://user-images.githubusercontent.com/91766546/155531566-2cfe5502-c295-488e-a5d5-ea74a8912e49.png)

![step26](https://user-images.githubusercontent.com/91766546/155531678-456f3def-ed17-4b17-97ed-1aa3b64b649e.png)

Step 8:
Our server is running and we can access it locally and from the Internet (Source 0.0.0.0/0 means 'from any IP address').
First, let us try to check how we can access it locally in our Ubuntu shell, run 'curl http://localhost:80' command

![step27](https://user-images.githubusercontent.com/91766546/155531982-61815c71-4fbd-44e6-9156-c886122cc154.png)

Step 9:
Now it is time for us to test how our Apache HTTP server can respond to requests from the Internet. 
Open a web browser of your choice and try to access following url 'http://<Public-IP-Address>:80'. Replace the '<Public-IP-Address>' with the public IP address of you server. You should be able to see this page displayed on your screen.
   
![step28](https://user-images.githubusercontent.com/91766546/155532443-b7e0b3d3-c16f-47e5-9fcc-d509f4a6ee2e.png)

Your web server is now correctly installed and accessible through your firewall.


## Installing MySql-Server
   
Now that we have our web server up and running, we need to install a [Database Management System (DBMS)](https://en.wikipedia.org/wiki/Database#Database_management_system) to be able to store and manage data for your site in a [relational database](https://en.wikipedia.org/wiki/Relational_database). [MySQL](https://www.mysql.com/) is a popular relational database management system used within PHP environments, so we will use it in our project.
   
Step 1:
Use ‘apt’ to acquire and install this software.

![step29](https://user-images.githubusercontent.com/91766546/155533662-cc88564f-2fca-4b00-b4bd-f52ffd8217f0.png)
   
When prompted, confirm installation by typing Y, and then ENTER.
   
![step30](https://user-images.githubusercontent.com/91766546/155534026-c558d6f7-5bd0-4817-b532-9e1ad3ae6fbc.png)

Step 2:
Next, run security script to remove insecure default settings and lock down access to your database system. Start the interactive script by running:

![step31](https://user-images.githubusercontent.com/91766546/155534470-0318e3c8-b579-4afa-8cc0-2008570bbd8e.png)
   
This will ask if you want to configure the VALIDATE PASSWORD PLUGIN. Answer Y for yes, or any other key to continue without enabling. I recommend not enabling this plugin for now and proceed by pressing N or any other key on your keyboard to go to the next step.

![step32](https://user-images.githubusercontent.com/91766546/155534959-7747fefe-c4e6-4711-b678-aa67f637f28a.png)

Your server will next ask you to select and confirm a password for the MySQL root user (The database root user is an administrative user with full privileges over the database system.)
   
Step 3:
By default, a MySQL installation has an anonymous user, allowing anyone to log into MySQL without having to have a user account created for them. You should remove this by typing 'Y' for each prompt that follows.

![step33](https://user-images.githubusercontent.com/91766546/155536247-2464ac1f-69cc-4482-893f-80d2cdfbd60f.png)
   
 Step 4:
 check whether you can log in to the MySQL console.
 
![step34](https://user-images.githubusercontent.com/91766546/155536485-e640bfa6-dc20-4f08-8b15-9bfea8a0ded0.png)
   
 To exit MySQL console, run:

![step35](https://user-images.githubusercontent.com/91766546/155536556-f3989116-f257-47a9-b7ba-5577a525ab6f.png)

 Your MySQL server is now installed and secured. Next, we will install PHP, the final component in the LAMP stack.
   
 ## Installing PHP
  
PHP is a script on the server-side used for the creation of Static or Dynamic Web sites or Web applications. PHP is a pre-processor for hypertext, which used to stand for home pages. The software used to build web applications is an open-source, server-side scripting language. We say a program designed for automated work by writing a script-based language (code lines). It is suitable for the output and construction of dynamic web pages for web applications, e-commerce applications, and database applications. PHP can be inserted into HTML.
   
Let's begin our installation.
   
Step 1:
To start with, run these three commands at once on your terminal.

![step36](https://user-images.githubusercontent.com/91766546/155537883-1fabfdb1-50d1-4ea6-9a5a-3d426acdb48f.png)
   
 Confirm Y for Yes when the prompt appears.

![step37](https://user-images.githubusercontent.com/91766546/155538002-db53a390-c5b9-4513-9d85-b542012e7df2.png)

Step 2:
Next, run the following command to check for the version of PHP installed.
   
![step38](https://user-images.githubusercontent.com/91766546/155538410-75057999-c06e-4d9d-b62b-f2194c1360f4.png)

### At this point, your LAMP stack is completely installed and fully operational.
   
To test your setup with a PHP script, it’s best to set up a proper Apache Virtual Host to hold your website’s files and folders.
We will configure our first Virtual Host in the next step.
   
## Creating a Virtual Host for your Website using Apache

 In this project, we will set up a domain called 'projectlamp', but you can replace this with any domain of your choice.
 
Step 1:
Apache on Ubuntu 20.04 has one server block enabled by default that is configured to serve documents from the '/var/www/html' directory. We will leave this configuration as is and will add our own directory next next to the default one.

Create the directory for `projectlamp` using 'mkdir' command
   
![step39](https://user-images.githubusercontent.com/91766546/155549854-fa0435b7-f5a4-4e60-a922-f9cd1fd845ff.png)

Step 2:
Next, assign ownership of the directory.
   
![step40](https://user-images.githubusercontent.com/91766546/155550126-115dce2f-2226-4816-bd6d-6861d7a90dd6.png)
   
Step 3:
Then, create and open a new configuration file in Apache’s 'sites-available' directory using your preferred command-line editor. 
   
![step41](https://user-images.githubusercontent.com/91766546/155550489-08ce1bce-e6a5-413f-84ec-82336e4f8873.png)
   
This will create a new blank file. Paste in the following configuration by hitting on 'i' on the keyboard to enter the insert mode, and paste the text.
  
![step42](https://user-images.githubusercontent.com/91766546/155550971-9b6b52c9-0f49-4e01-868c-4749be5f5d7c.png)
   
To exit the text editor press Esc key on your keyboard and type :wq (w for write and q for quit) and then hit Enter key.
   
Step 4:
Use the 'ls' command to see the contents of the sites-available directory.
  
![step43](https://user-images.githubusercontent.com/91766546/155551580-f407a9e0-771b-4c43-91ea-6942af1fff17.png)
   
You will see something like this on your terminal screen.
   
![step44](https://user-images.githubusercontent.com/91766546/155551713-82ecb0c8-9eb9-4e08-b503-81f054767b0d.png)
   
Step 5:
You can now use 'a2ensite' command to enable the new virtual host.
   
![step45](https://user-images.githubusercontent.com/91766546/155552049-78ebb962-3d6e-402c-ad8a-56a8e22e30be.png)
   
![step46](https://user-images.githubusercontent.com/91766546/155552456-bc2172b5-2ebb-4aca-b6a7-c90e13861ea6.png)

You might want to disable the default website that comes installed with Apache. This is required if you’re not using a custom domain name, because in this case Apache’s default configuration would overwrite your virtual host. To disable Apache’s default website use a2dissite command.
     
![step47](https://user-images.githubusercontent.com/91766546/155552407-00016452-a794-4834-8e41-891ddddf3983.png)
   
![step48](https://user-images.githubusercontent.com/91766546/155554242-3fae5a9a-52d1-4e41-8836-915a7ac86022.png)

Step 6:
To make sure your configuration file doesn’t contain syntax errors, run the following command.
 
![step49](https://user-images.githubusercontent.com/91766546/155555156-c0b51016-b126-426c-8f5d-472358ef3f4e.png)
  
You should see something like this on your screen.
   
![step50](https://user-images.githubusercontent.com/91766546/155555413-8dd8d68f-3ec1-4227-bcc3-312a10b6a268.png)
   
Step 7:
Finally, reload Apache so these changes can take effect.
 
![step51](https://user-images.githubusercontent.com/91766546/155555673-d318b83c-814b-4af7-bc0b-3eda8badeac3.png)
   
  Congratulations! Your new website is now active!!!
  
Step 8:
Create an index.html file in that location so that we can test that the virtual host works as expected.
 
 ![step52](https://user-images.githubusercontent.com/91766546/155556522-fd921fee-dfd8-437a-a4c9-48c76bac5cea.png)
 
 Step 9:
 Next step is to go to your browser and try to open your website URL using your public IP address. Use http://<Public-IP-Address>:80 and replace the <Public-IP-Address> with your own IP address. 
 You should see something similar to this on your browser.
   
![step53](https://user-images.githubusercontent.com/91766546/155560956-db1d4b47-6552-4ae3-ab3d-30fecb1f62de.png)

You can leave this file in place as a temporary landing page for your application until you set up an index.php file to replace it. Once you do that, remember to remove or rename the index.html file from your document root, as it would take precedence over an index.php file by default.
   
   ## Enable PHP on the website
We are at the final stages of our project. In order to enable PHP on the website the the default DirectoryIndex settings on Apache will have to change for the index.php file to take precedence over the index.html file. Let's change that now.
   
Step 1:
You’ll need to edit the '/etc/apache2/mods-enabled/dir.conf' file and change the order in which the index.php file is listed within the DirectoryIndex directive.
 
![step55](https://user-images.githubusercontent.com/91766546/155558696-f332dd79-5c61-4fe9-9e0a-5a5853ca7838.png)
   
You will need to change the order of the files listed from this:
   
   
![step56](https://user-images.githubusercontent.com/91766546/155558724-afe22a14-429d-4b31-a97c-360f1f8ebe2b.png)
   
To this one. 
   
![step57](https://user-images.githubusercontent.com/91766546/155558749-f6496e95-edba-4d99-a606-27794d5adf7c.png)
   
Step 2:
After saving and closing the file, you will need to reload Apache so the changes take effect.
   
![step58](https://user-images.githubusercontent.com/91766546/155559166-23096632-faf5-43fe-b8b5-c4da36985ae6.png)

Step 3:
Finally we will create a PHP file to test if PHP is correctly installed in our server. Let's create a new file named index.php inside our custom web root folder.
     
![step59](https://user-images.githubusercontent.com/91766546/155559633-2b5bd2be-fb91-4d3d-81aa-bbb058cf37d6.png)
   
This will open a blank file. Add the following text, which is valid PHP code, inside the file.
   
![step60](https://user-images.githubusercontent.com/91766546/155559928-5321b9d0-0131-4f8d-9023-1440ec365c65.png)
   
After saving and closing the file now go to your browser and refresh the page to see a page similar to this one.
   
![step61](https://user-images.githubusercontent.com/91766546/155560159-75244c8a-7f15-4d23-933a-555842519312.png)
   
Step 4:
After checking the relevant information about your PHP server through that page, it’s best to remove the file you created as it contains sensitive information about your PHP environment -and your Ubuntu server.
   
![step62](https://user-images.githubusercontent.com/91766546/155560237-23aea492-d0cb-4f09-8b5f-99e5f9c024fe.png)

This is the end of our project. We have successfully implemented our LAMP stack on an AWS EC2 server.
