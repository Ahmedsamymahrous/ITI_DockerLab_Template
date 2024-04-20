# ITI - Docker Lab 🐋

## Task 1: Working with Docker Hello-world Image
### Objective
Learn how to run a container using the hello-world image and manage containers and images.

### Steps
#### 1. Run a Container with hello-world Image
```bash
docker run hello-world
```
#### 2. Check Container Status and Explain
```bash
docker ps -a
Exit , because the hello-world print a message to the console, and then exit .
```
#### 3. Start the Stopped Container
```bash
docker start eb5806fff4c1
```
#### 4. Remove the Container
```bash
docker rm eb5806fff4c1 
```
#### 5. Remove the Image
```bash
docker rmi -f hello-world
```
---

## Task 2: Running Container with Ubuntu Image
### Objective
Run an Ubuntu container in interactive mode, create a file inside it, and manage containers.

### Steps
#### 1. Run Ubuntu Container in Interactive Mode
```bash
docker run -it ubuntu
```
#### 2. Create a File inside the Container
```bash
touch hello-docker
```
#### 3. Stop and Remove the Container
```bash
docker stop serene_bassi
docker rm serene_bassi
```
#### 4. Check File Status
```bash
removed
```
#### 5. What happened to hello-docker file?
```bash
removed
```
#### 6. Remove All Stopped Containers
```bash
docker rm  amazing_engelbart

```
#### 7. Bonus: Remove All Containers in One Command
```bash
docker container prune -f
```

---
## Task 3: Creating a Custom Nginx Docker Image
### Objective
Create a custom Docker image using Nginx and a local HTML file.

### Steps
#### 1. Create a Local HTML File
```bash
vi index.html
```
#### 2. Write Dockerfile and Copy the HTML file to the Docker Image
```bash
FROM nginx                                                                       
COPY index.html /usr/share/nginx/html/index.html 
```
#### 3. Run Container with New Image
```bash
docker build -t custom-nginx .
```

#### 4. Test the Container, open your browser and navigate to http://localhost:8088 to check if everything is okay
```bash
docker run -d -p 8088:80 custom-nginx
everything is okey
```

