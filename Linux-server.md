#### To create a linux server on AWS , first i created an account on the Amazon Web Service and launched an instance. While launching the instance i chose a name for the instance, chose ubuntu (linux distribution) created a key pair and a new security group


![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/e9f9f072-b6da-4677-a45d-8dd5c68ede08)




#### Now my instance is ready 

![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/4f2c04c7-b96a-4049-a423-e75b63c88182)




#### Next, i am going to connect my AWS virtual server to my ubuntu terminal. i will do this by ssh into the terminal. i will copy my public ip address and change directroy into where my private key is saved.

![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/9ef7b787-c8d3-4ba3-845d-191b8115ce4f)




#### Now, i have established a successful connection using my Mobaxterm machine

![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/ff000b83-f3f4-47dd-8892-064b44d30edb)




#### Using the package manager APT i ran "sudo apt update" 

!![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/71648b46-426a-44ab-b1de-1c5eb657eb54)



#### Using the command "sudo apt install tree" i installed tree on the server 
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/6448e0f0-c85d-4c55-ae05-b39c792870f5)




#### I verified the installed "tree" by running "tree ~" command 
!![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/8753a454-6f26-4a3d-9f8e-70488ea0ed0c)


#### Next, i updated installed packages to keep my system up-to-date by running "sudo apt upgrade"
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/c8dacfa5-f178-476b-8809-30c9a163ab67)


#### Next, i removed the "tree" that was installed earler by runmning the command "sudo apt remove tree"
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/1613343a-5496-4c07-97e9-e369f1e229f6)


#### I also installed and removed Nginx by running the command "sudo apt install Nginx" and "sudo rm -r Nginx"
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/466eafce-8782-4ffc-aff8-540d606cd5aa)




#### That is the end of this project.












