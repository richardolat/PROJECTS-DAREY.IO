## AWS S3 BUCKET POLICY EXPLORATION: This mini project is about using the s3 policy to control access to the s3 bucket


1. #### I logged on to my AWS account and navigated straight to the S3 Service 
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/d92e063c-8893-4073-9484-8d45aa94a14a)







2. #### I created an S3 bucket and named it richies3project
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/e2f033e5-c2d9-48ae-8416-d5430b00719b)









3. #### Next, i will upload an html file here
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/fa25c1ab-3e24-442b-8cc0-9059f566ea8b)








4. #### I uploaded the html file as an object inside the bucket
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/2ffda224-be41-4f72-8c22-921225dc5e21)









5. #### I unblocked public access under the permissions
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/7c51213c-d7ec-418a-9536-6d7c0d491d58)









6. #### I moved to the policy generator to generate policy for my bucket 
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/d74635e1-7ad1-4187-a362-0c97ee6dda03)








7. #### I generated the JSON-formatted policy
  ![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/df2e6e50-bf59-4eab-a49b-0ddc8a25a1ec)











8. #### I added the generated policy
   ![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/5aa522ae-4dbd-4437-9174-697371d9e6a1)








9. #### The policy has been put in place
   ![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/056c4bbd-9bfc-4cb2-8ce9-0440d5ffeacd)










 10. #### After adding the JSON-formatted policy, i tried accessing the object url and it gave me an access denied response
     ![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/726edc40-312e-4d77-9d4a-f13380d2bd81)









11. #### So, i went back to the object, clicked on it and clicked on action later. under i enabled "Make Public Using CLI"  
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/2f84b7fe-570b-49c9-b991-2a453b38271b)










12. #### My object is ready and deployed.
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/fc0788c9-b4bb-4ca4-895c-f4d238023a47)


















































































