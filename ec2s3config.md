#### I logged into the AWS console as John-Developer and launched an Instance
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/3a0fb03a-5ae7-4822-ab2b-edfe67398f7f)




#### I associated an Elastic IP with the instance created
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/b9b36b28-5c63-4f88-8d0a-9b69f8397117)






#### I logged into the AWS console as Mary-Analyst and created an s3 bucket
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/d4cf3a74-8ab5-47fc-a108-248456c43cc4)




#### I created an index.html file on my computer and added "Welcome to Amazon s3" content into it. I then uploaded the file into my bucket
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/ede758c6-87a5-45bd-aa2e-b0f8009b2211)






#### I configured the S3 bucket for web-hosting by enabling the static website hosting
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/2113cd62-38e3-4c50-8112-3a98b99c77db)





#### I successfully enabled the website hosting for my bucket
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/58b59066-a821-4c4e-8603-8432b1e36cf7)







#### On my Ec2 instance, i installed Nginx web server by running the command "sudo apt update -y && sudo apt install nginx -y"
 ![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/dbda2ebd-9f02-4403-a4cc-72e3a2330ed7)







#### I configured the webserver to serve my S3 app directly. I created and editted a file name "mybucket" by running the command "sudo nano /etc/nginx/sites-available/mybucket"
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/178938ee-e424-4260-ab64-d8274a0b2fee)








#### I put a configuration code inside the file
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/1b143cc4-d4ef-49ba-90a3-17bf39df8b3e)





#### My Nginx reverse proxy is up and running. Listening on port 80 on my webserver 
![Screenshot 2024-05-28 132715](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/5efc4c0d-269d-49c5-b659-ed44d8b8d743)






#### I made my index file public 
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/1e59be98-e2cc-43d6-bac3-aaa45e865f63)







#### 



































































