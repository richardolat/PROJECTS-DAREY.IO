## VIRTUAL PRIVATE CLOUD 



#### I navigated to the VPC console
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/69bbe730-3e4f-4ec8-9a52-d93d8074805d)






#### I filled up the details on the VPC page
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/a243b70b-6579-4cba-9e8c-63a52511fb8d)







#### My VPC is created and ready. 
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/6317781e-758b-4467-b965-0579034f2bb8)




#### Note: I got the IPv4 CIDR from [Ipv4 CIDR] (https://datatracker.ietf.org/doc/html/rfc1918)



## SUBNET



#### Next, I move to create a subnet to be able to split and work under different network IP from the Base IP chosen from the VPC
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/0fec671c-4648-4f84-a826-acb27632db50)






#### The two subnets created are ready
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/96701826-6bea-42a4-918f-399980d56ad1)






#### The subnet IPV4 CIDR was calculated using (https://cidr.xyz/)
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/cd5731a2-19a4-4637-b81e-bbb899ea7c40)




## ROUTE TABLE


#### To make the network IP private and public, I moved to the Route table
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/7e6314bd-c6b8-4676-99a3-eba7e1d259e4)








#### The Route Table is successfully created 
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/e24bd411-c744-4b5a-aaed-e6e2aa77edba)









#### After creating the Route Table, I attached the public subnet to the Subnet-association
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/f380aa44-27db-4066-a340-329485d55508)











#### From there, I moved to the internet gateways
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/399f1078-2afc-4fe8-95ec-7746c5b6e2a4)









#### I filled in the details and clicked **Create Internet Gateways**
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/5cbcd5b5-077e-4173-b844-3bd81564a345)









#### Internet Gateways is ready 
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/52866ab6-25c5-416d-9f82-ea5e73555e1f)








#### Next, I clicked on Action and attached the VPC
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/5eb36a41-0fa4-4e2a-87db-afb372fe5bcc)










####  Internet Gateways successfully attached to VPC 
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/ddd8ec05-a693-412f-8552-ef140636e1c2)









#### Then, back to the Route Table, edit route and attach the Internet gateways
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/570695f1-379e-4c48-b6e0-94a8acd65b18)








#### Created another route table for private IP network
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/ae77229b-0014-4398-86ff-83aaa4620568)








#### Then attach the private subnet into the route table
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/ce97c293-e03b-41fb-b7b0-ed242acdc327)







#### Then, next to NAT Gateways for private subnet network 
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/e829bcc2-8ef9-47ac-b1f9-d76879739e67)









#### Details filled for NAT Gateways 
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/e34cfa34-db6a-4338-98d5-f21dee1ce9de)







#### NAT Gateways is available 
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/d319702f-38be-4c91-b1cc-486c4ab25b0d)








#### Back to the Route Table, the route is edited.
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/b4620314-3a07-4fd9-9deb-aeffb5f85e85)








 #### THAT IS THE END OF THE PROJECT. THANK YOU.









































































































































