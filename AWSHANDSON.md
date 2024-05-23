3 SETTING UP IAM ACCOUNT FOR A BACKEND DEVELOPER, JOHN AND DATA ANALYST, MARY ON MY ROOT ACCOUNT






#### On the IAM console, i clicked on Policy and created
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/c2a3cf75-4cf2-441e-abdf-1173f8457b25)






#### I created an EC2 full access Policy for the developers
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/fbb99628-13b2-48e4-a3ee-e14e76ef0a60)






#### I also created a S3 full access policy for data-analysts
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/2eae1067-257b-486a-a8a8-3097e47bf0dc)








#### I created users group for the development team 
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/cf616ba1-a5aa-4fe8-999f-fda223f2fe88)









#### I created data analysts user group also
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/41c2ee68-813d-4f1e-95aa-eba1a23f40e3)








#### I created a user named "John-developer" and added him to the Development-team
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/6d132aeb-8dee-43d2-82ac-bf3e637e0b8f)








#### I created another user named "Mary" and added her to the Data-Analysts_Team
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/86142e69-2f2b-471c-899a-8630e34ab2c8)





#### I logged into the console as John-developer and created an ec2 instance 
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/eda95d73-503e-4fc2-b371-482dcd080fbf)





#### I attempted to create an s3 bucket with the John account and it said permission was denied. This means that John's permission was successfully set
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/2e5d162f-fd77-4d29-99f8-35c9363c2044)





#### I logged into Mary-Analyst and created an s3 bucket successfully 
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/201752fd-d7d3-4445-a132-f8c98dcc4061)





#### I attempted to create an instance with the Mary-analyst account and i got an unauthorised permission error. This means Mary's permission was successfully set
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/d9579c08-7973-418c-9a33-78154d13e277)


























































































