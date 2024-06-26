# CAPSTONE PROJECT: INTRODUCTION TO CLOUD COMPUTING



#### I created a directory named "Marketpeak_Ecommerce" 
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/d0ac6968-2acc-4d97-9c15-b190529e09f4)







#### I Changed directory [cd] into the newly created directory and initiate a Git repository by running the command "cd MarketPeak_Ecommerce, git init"
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/5a0b268f-04c8-4c60-8110-ca51c8676d56)





#### I downloaded a website template, extracted it and added it into my "Marketpeak_Ecommerce" directory
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/37d88ac1-732b-45f1-ab8f-32e62cd52e56)





#### I staged the extracted website template into my git respository by running the command "git add 2130_waso_strategy "
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/1d564024-002e-4534-af30-1d18dffa95c0)








#### I checked if the staged changes was successful 
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/39385b6b-27ed-4b35-9bac-ad7ee61ae2ef)







#### I set my git global configuration with my username and email
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/06b195b6-b3ca-4353-a266-9fdaa756c023)







#### I committed the staged changes by running the command "git commit -m "Initial commit with basic e-commerce site structure"
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/ce2cab4f-41c0-48b2-882e-863d38f462d7)





#### I created a git repository without any initialization and pushed my local respository content into it

![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/ade960c5-7b23-4818-b241-0db60f94ff70)

![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/8c4106ab-a150-472a-80e3-95e17a9013e2)






#### Within my project directory, I added my remote repository url to my local repository configuration
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/623f8890-bf5d-40b1-87c9-752fbfec5175)




#### I uploaded my local repository content into github
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/d8a9d265-ad79-4aa2-b78f-cb11ad0366cb)






#### I set up an Ec2 account with Amazon Linux AMI
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/89a204b8-d386-433f-9df1-0d6831fddc63)






#### I connected to the instance using SSH 
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/9474e1b6-3e06-43f4-b223-f199669693b6)





#### I proceded to authenticating my github by cloning the repository with ssh
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/513ac0c6-ad4e-4af2-a8f8-8f2bba389ddf)



#### I generated SSH keypair using "ssh-keygen"
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/2d13bfea-0be7-44b9-8273-b43d73e1953d)






#### After generating the keypair i displayed and copied the public key
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/e5b5049b-1ab7-4e01-b2fe-8a8311815ceb)








#### I added the SSHkey to my github
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/36e53fe6-a44a-4b28-9f94-6a6bece24965)







#### I cloned the repository using the SSH url by running the command " git clone git@github.com:richardolat/Marketpeak_Ecommerce.git"
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/cc4535c2-df7f-4024-b8a0-0ba10cca4a59)





#### I installed a web-server on my Ec2 by running the commands; "sudo yum update"
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/a2470755-4780-4513-bb57-3000d80e7cb1)






#### I installed Apache2 by running the command "sudo yem install httpd -y"
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/3bd1c8c7-bb26-40f7-b481-118568e46973)








#### I started the httpd and enabled it by running the commands; "sudo systemctl start httpd"  "sudo systemctl enable httpd"
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/658d1eb8-11fa-4420-9d4a-110f745daff3)







#### I moved to configure httpd for website by clearing the default httpd web directory. i did that by running the command "sudo rm -rf /var/www/html/*"
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/ebeda5b2-67d3-46f1-9ca0-d7a380cf06ae)






#### I then copied the Marketpeak Ecomerce into it by running the command  "sudo cp -r ~/Marketpeak_Ecommerce/* /var/www/html/"
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/4636128f-788e-422d-9c28-3962ecd8d07c)







#### I applied the changes by reloading the httpd server by running the command "sudo systemctl reload httpd"
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/fd8a42cc-13af-4656-b94c-f42c622acde3)








#### I opened my web browser and access the IP of my EC2 to view the deployed website
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/685b0515-bfea-4c73-969b-b7afa5bddf0c)




## CONTINOUS INTEGRATION AND DEVELOPMENT WORKFLOW









#### i continued my development work by creating a new branch 
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/da54a5f9-5221-4d20-bbac-72ed9ad8ad5b)





#### I staged my changes by running the command "git add 2130_waso_strategy" 
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/baec3137-5b3e-4061-b4a5-54a9c7f678fd)








#### I commit my change in the git repository by running the command " git commit -m "Add new features or fix bugs"
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/0afd9dbf-eb46-486d-b7cf-5adabb58eccb)









#### I uploaded the development branch with the new changes on github by running the command "git push origin development
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/c3b8584b-7151-4d50-b062-01f1fff45eb2)










#### On my github, i created a pull request and merged the development branch with the main branch  
![Screenshot 2024-05-30 134607](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/3ee4cd70-9216-4591-a08f-376e9509fc45)









#### I reviewed the changes for any potential issue 
![Screenshot 2024-05-30 134803](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/58ece10e-3b43-46e9-8703-6664ac842610)













#### I created a pull request to merge the development branch into the main branch
![Screenshot 2024-05-30 135230](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/30b92fcd-0dac-430c-a616-94b75b19203c)









#### I swicthed to the main branch by running the command "git checkout main"
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/b88bb560-f910-4af9-b1c3-2d4e9da1c73c)







#### I merged the pull request into the main branch by running the command "git merge development"
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/f42e4040-61de-407f-a23b-61ab6eaa2d9d)








#### I pushed the merged changes to github by running the command "git push origin main"
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/e8fd63e0-e0e4-4c6c-a82b-36d90b742f9b)







#### I navigated to the production server where the production website is hosted and pull the latest changes from the main branch by running the command "git pull origin main"
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/501c9f29-9a31-4661-9dfc-b6a2c4435fe3)





































































































































































































