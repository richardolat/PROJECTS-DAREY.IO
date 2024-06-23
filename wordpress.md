## WORDPRESS SITE ON AWS


#### Create VPC 
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/b9095135-646e-4071-9ffe-35aabbe15017)




#### Create internet gateway and attach it to the VPC
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/ac9aa26b-0203-4f7c-817b-91c79ed70013)




#### Create two Public subnets in two avalailabity zones and modify it to enable auto-assign public IP
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/c90a5809-f888-440f-b0cc-8cb1c0b27af6)




#### Create a public Route Table; Edit the route to enable internet-gateway and associate the public-subnet
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/f30cc153-9e3c-4f22-ad72-94731e16d88a)




#### Create four private subnets. Two for the app and two for database
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/89aeae67-e334-4d90-8017-b6a3252c2235)





#### Create a route table for the private subnets 
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/0d472c14-92fd-440c-a992-633fe3f92086)






#### Allocate Elastic IP address for the NATgateway in Public subnet-1 and Public subnet-2
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/760cb54f-b71a-4485-b3c5-3924fb2913f7)






#### Create two NAT gateway with the public subnet 1 and 2 and then add it to the private route table 1 and 2  to enable it access internet
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/d9bed200-033d-4c90-97e0-bb4da8061087)






 #### Create security group for the Loadbalancer; Web-server; Database and Elastic file system (EFS) with the right rules
 ![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/fa3ebda1-6465-4d61-a3e7-e416a3b51744)





#### Create database subnet group
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/e9ab8de7-6168-4279-914c-7c12f2c9c4d0)



#### Create and configure Database
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/110c6ef6-0e09-499d-8d1c-307e41d5792a)




#### Create Elastic File System
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/29ead968-2688-4682-baa4-116c4e2649fc)





#### Create an EC2 instance 
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/ad31253b-7452-4a37-a7cd-fe45fcf032f1)






#### SSH into the EC2 instance and change to root
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/b44460ee-daab-4e9e-a2ca-ca5ef62aadbe)






#### Run "yum update -y" to update the webserver
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/ae9799cc-e8fe-4a2e-adaa-4ad3694d3e05)






#### Make a directory to mount the EFS file "mkdir -p /var/www/html"
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/c8a8186d-03e6-4a91-9522-6487f6443277)






#### Mount the EFS file into the newly created directory "sudo mount -t nfs4 -o nfsvers=4.1,rsize=1048576,wsize=1048576,hard,timeo=600,retrans=2,noresvport fs-0a03cac5dddf1f3e5.efs.us-east-1.amazonaws.com:/ /var/www/html"
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/695b9c27-3ade-4d28-b80b-d70140db5b17)



#### Install httpd and its dependencies "sudo yum install -y httpd httpd-tools mod_ssl"
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/f11e9ecb-240d-461f-8624-fe8d272d1d12)




#### Enable and start the httpd by running the command "systemctl enable httpd" "systemctl start httpd"
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/48b9fae0-aded-444b-98bf-4c6f9197c3d7)




#### Install php by running "sudo yum install php" (The command "sudo yum install -y httpd httpd-tools mod_ssl" didnt work on my configured amazon-linux)
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/fa9bd77f-2c4c-4494-bb7d-73dd522ef364)





 #### Clean metadata by running the command "sudo yum clean metadata"
 ![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/df4c7b17-3887-430d-96d9-02b255394ef1)





#### Run the command "sudo yum install php php-common php-pear -y"
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/0c48b384-6cc4-45fe-9ab5-a11a9dfbf17e)





#### Run the command "sudo yum install php-{cgi,curl,mbstring,gd,mysqlnd,gettext,json,xml,fpm,intl,zip} -y" to install other php dependencies 
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/e0e11530-ac35-4a45-9666-2117e1ada5e1)



## Install mysql5.7


#### run the command "sudo rpm -Uvh https://dev.mysql.com/get/mysql57-community-release-el7-11.noarch.rpm"
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/5934a7c0-5109-452e-b890-74f8610b2966)































































































































































































































 








































