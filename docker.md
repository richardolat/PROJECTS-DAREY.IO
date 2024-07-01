##  Project Name: nginx Docker and Kubernetes Tutorial Description: The "nginx Docker and Kubernetes Tutorial" project aims to provide a step-by-step guide on how to containerize a simple HTML and CSS web application using Docker and deploy it to a Kubernetes cluster using kind. 
## The project's main goal is to help individuals who are new to Docker and Kubernetes understand the process of building and deploying containerized applications. 
## By following the provided documentation, users will learn how to create a Dockerfile, build a Docker image, push it to Docker Hub, set up a Kubernetes cluster using kind, deploy the Docker image to the cluster, and expose the application using a Kubernetes service.






#### Create a new directory: "mkdir myapp"
![Screenshot 2024-06-30 152315](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/ee33de40-d4a6-4845-b2e8-697225af1825)





#### Change directory into the new directory: "cd myapp"
![Screenshot 2024-06-30 152433](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/92bd3d25-00ec-4aee-9396-a7521dc9bd1c)







#### Inside the directory, create an HTML file (index.html) and CSS file (style.css): "touch index.html style.css"
![Screenshot 2024-06-30 153442](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/e35d0dea-fe06-4b50-8358-b1aee33140da)






#### Initialize a Git repository in the project directory: "git init"
![Screenshot 2024-06-30 154225](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/aefa33b2-ee7d-4c17-b0b2-dcef2fbeb626)






#### Add and commit the initial code to the Git repository: "git add . git commit -m "Initial commit"
![Screenshot 2024-06-30 154705](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/c8e08372-bedb-48f8-89f7-0811c7eea984)







#### Create a Dockerfile specifying Nginx as the base image:
  Create a new file called `Dockerfile` and open it in a text editor. Add the following content to the file:
FROM nginx:latest
COPY index.html /usr/share/nginx/html
COPY style.css /usr/share/nginx/html
![Screenshot 2024-06-30 155204](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/26c6ca08-f208-4196-a877-a6f1e90c370d)





#### Log in to Docker Hub: "docker login"
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/8d66f167-308a-46ff-ba97-cff3c7914b0f)







#### Build and push the Docker image to Docker Hub:docker build -t your-dockerhub-richiehub/my-nginx-app .
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/ad82fa2d-d168-44e1-8578-cbab5b970b10)










#### 






















































