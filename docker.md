##  Project Name: nginx Docker and Kubernetes Tutorial by OLATUNDE OLABODE RICHARD
## Description: The "nginx Docker and Kubernetes Tutorial" project aims to provide a step-by-step guide on how to containerize a simple HTML and CSS web application using Docker and deploy it to a Kubernetes cluster using kind. 
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
























#### Push the Docker image to Docker Hub: "docker push richardolat/nginx:1.0.0"
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/48dcfcfb-f014-4ec3-b3bf-5eb877f0b397)





















#### Install kind (Kubernetes in Docker):
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/a50026eb-cba5-420e-b62f-125ae384ab6f)






















#### Create a kind cluster:"kind create cluster"
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/04e5a4b7-57a9-47e5-b2d3-5f6a962e1420)























#### Create a Kubernetes deployment YAML file (deployment.yaml) specifying the image and desired replica count:
Create a new file called `deployment.yaml` and open it in a text editor. Add the following content to the file:
```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: my-nginx-app
spec:
  replicas: 1
  selector:
    matchLabels:
      app: my-nginx-app
  template:
    metadata:
      labels:
        app: my-nginx-app
    spec:
      containers:
      - name: my-nginx-app
        image: your-dockerhub-username/my-nginx-app
        ports:
        - containerPort: 80
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/0b826264-c16d-4d46-afe4-f652a1bae32a)


















#### Apply the deployment to the cluster: "kubectl apply -f deployment.yaml"
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/27654f32-d0c5-4654-b9e2-42c773923140)























#### Create a Kubernetes service in a YAML file (service.yaml) specifying the type as ClusterIP:
Create a new file called `service.yaml` and open it in a text editor. Add the following content to the file:
```yaml
apiVersion: v1
kind: Service
metadata:
  name: my-nginx-service
spec:
  selector:
    app: my-nginx-app
  ports:
    - protocol: TCP
      port: 80
      targetPort: 80
  type: ClusterIP
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/71f02b8a-e72a-49f2-8f34-879fb7b97f14)




























#### Port-forward to the service to access the application locally:"kubectl port-forward service/my-nginx-service 8080:80"
![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/187d1c84-c297-49e5-9d38-f8429897c42f)






















#### Open the browser and visit `http://localhost:8080` to view the simple frontend application.

![image](https://github.com/richardolat/PROJECTS-DAREY.IO/assets/134428528/8d98ef99-ceca-41f9-a234-4e8995d02e1a)




































































































































