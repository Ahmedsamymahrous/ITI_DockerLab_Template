# ITI - Docker Lab 🐋

## Task 1: Working with Docker Hello-world Image
### Objective
Learn how to run a container using the hello-world image and manage containers and images.

### Steps
#### 1. Run a Container with hello-world Image
```bash
nagy_disappointed@Nagy:~$ sudo docker run hello-world

Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://hub.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/get-started/
```
#### 2. Check Container Status and Explain
```bash
nagy_disappointed@Nagy:~$ sudo docker images
REPOSITORY    TAG       IMAGE ID       CREATED         SIZE
hello-world   latest    d2c94e258dcb   11 months ago   13.3kB
nagy_disappointed@Nagy:~$ sudo docker ps
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
nagy_disappointed@Nagy:~$ 


# Explain
the docker container has finished

```
#### 3. Start the Stopped Container
```bash
nagy_disappointed@Nagy:~/dockerLabs$ ls
Dockerfile
nagy_disappointed@Nagy:~/dockerLabs$ sudo docker images
REPOSITORY    TAG       IMAGE ID       CREATED         SIZE
sleepe        v2        60c00852ddc2   9 days ago      77.9MB
sleepe        latest    96ebc284383f   9 days ago      77.9MB
hello-world   latest    d2c94e258dcb   11 months ago   13.3kB
nagy_disappointed@Nagy:~/dockerLabs$ sudo docker run -d sleepe:v2
d2438021399c7bc753fb5d1993ea025a301e066f43277ef180a474154be57171
nagy_disappointed@Nagy:~/dockerLabs$ sudo docker ps
CONTAINER ID   IMAGE       COMMAND         CREATED         STATUS         PORTS     NAMES
d2438021399c   sleepe:v2   "sleep 80000"   8 seconds ago   Up 8 seconds             compassionate_hellman
nagy_disappointed@Nagy:~/dockerLabs$ sudo docker stop  compassionate_hellman
compassionate_hellman
nagy_disappointed@Nagy:~/dockerLabs$ sudo docker start compassionate_hellman
compassionate_hellman
nagy_disappointed@Nagy:~/dockerLabs$ sudo docker ps
CONTAINER ID   IMAGE       COMMAND         CREATED              STATUS         PORTS     NAMES
d2438021399c   sleepe:v2   "sleep 80000"   About a minute ago   Up 6 seconds             compassionate_hellman
nagy_disappointed@Nagy:~/dockerLabs$ 
```
#### 4. Remove the Container
```bash
nagy_disappointed@Nagy:~/dockerLabs$ sudo docker ps
CONTAINER ID   IMAGE       COMMAND         CREATED         STATUS         PORTS     NAMES
d2438021399c   sleepe:v2   "sleep 80000"   3 minutes ago   Up 2 minutes             compassionate_hellman
nagy_disappointed@Nagy:~/dockerLabs$ sudo docker rm -f compassionate_hellman
compassionate_hellman
nagy_disappointed@Nagy:~/dockerLabs$ sudo docker ps
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
nagy_disappointed@Nagy:~/dockerLabs$ 
```
#### 5. Remove the Image
```bash
nagy_disappointed@Nagy:~/dockerLabs$ sudo docker rmi -f sleepe
Untagged: sleepe:latest
Deleted: sha256:96ebc284383faff5a7edd5c573eb75c924c7729066014eae4cf6691210fc5487
nagy_disappointed@Nagy:~/dockerLabs$ 
```
---

## Task 2: Running Container with Ubuntu Image
### Objective
Run an Ubuntu container in interactive mode, create a file inside it, and manage containers.

### Steps
#### 1. Run Ubuntu Container in Interactive Mode
```bash

```
#### 2. Create a File inside the Container
```bash
```
#### 3. Stop and Remove the Container
```bash
```
#### 4. Check File Status
```bash
```
#### 5. What happened to hello-docker file?
```bash
```
#### 6. Remove All Stopped Containers
```bash
```
#### 7. Bonus: Remove All Containers in One Command
```bash
```

---
## Task 3: Creating a Custom Nginx Docker Image
### Objective
Create a custom Docker image using Nginx and a local HTML file.

### Steps
#### 1. Create a Local HTML File
```bash
```
#### 2. Write Dockerfile and Copy the HTML file to the Docker Image
```bash
```
#### 3. Run Container with New Image
```bash
```

#### 4. Test the Container, open your browser and navigate to http://localhost:8088 to check if everything is okay
```bash
```

