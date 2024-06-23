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












































































 








































