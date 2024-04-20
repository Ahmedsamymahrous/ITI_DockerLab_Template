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
nagy_disappointed@Nagy:~/dockerLabs$ sudo docker pull fedora
Using default tag: latest
latest: Pulling from library/fedora
353b74d8db1c: Pull complete 
Digest: sha256:61864fd19bbd64d620f338eb11dae9e8759bf7fa97302ac6c43865c48dccd679
Status: Downloaded newer image for fedora:latest
docker.io/library/fedora:latest
nagy_disappointed@Nagy:~/dockerLabs$ sudo docker run fedora
nagy_disappointed@Nagy:~/dockerLabs$ sudo docker run -it fedora
[root@4c88f210d489 /]# echo "hello world"
hello world
[root@4c88f210d489 /]# 

```
#### 2. Create a File inside the Container
```bash
nagy_disappointed@Nagy:~/dockerLabs$ sudo docker ps
CONTAINER ID   IMAGE       COMMAND         CREATED         STATUS         PORTS     NAMES
4c91213bff61   sleepe:v2   "sleep 80000"   3 minutes ago   Up 3 minutes             kind_heyrovsky
nagy_disappointed@Nagy:~/dockerLabs$ sudo docker exec -it kind_heyrovsky /bin/bash
root@4c91213bff61:/# touch file2
root@4c91213bff61:/# 

```
#### 3. Stop and Remove the Container
```bash
nagy_disappointed@Nagy:~/dockerLabs$ sudo docker rm -f kind_heyrovsky
kind_heyrovsky
nagy_disappointed@Nagy:~/dockerLabs$ 

```
#### 4. Check File Status
```bash
nagy_disappointed@Nagy:~/dockerLabs$ sudo docker run -d sleepe:v2
b417440a593e327a087cdb1c49de7429d6dc996340290138f4cbc1f0b4715f92
nagy_disappointed@Nagy:~/dockerLabs$ sudo docker ps
CONTAINER ID   IMAGE       COMMAND         CREATED          STATUS          PORTS     NAMES
b417440a593e   sleepe:v2   "sleep 80000"   18 seconds ago   Up 16 seconds             pensive_pike
nagy_disappointed@Nagy:~/dockerLabs$ sudo docker exec -it pensive_pike /bin/bash
root@b417440a593e:/# ls
bin   dev  home  lib32  libx32  mnt  proc  run   srv  tmp  var
boot  etc  lib   lib64  media   opt  root  sbin  sys  usr
root@b417440a593e:/#
```
#### 5. What happened to hello-docker file?
```bash
the file was not found 
```
#### 6. Remove All Stopped Containers
```bash
nagy_disappointed@Nagy:~/dockerLabs$ sudo docker ps -a
CONTAINER ID   IMAGE          COMMAND         CREATED          STATUS                      PORTS     NAMES
b417440a593e   sleepe:v2      "sleep 80000"   3 minutes ago    Up 3 minutes                          pensive_pike
4c88f210d489   fedora         "/bin/bash"     11 minutes ago   Exited (0) 11 minutes ago             boring_gates
d0a61e5bfb9d   fedora         "/bin/bash"     12 minutes ago   Exited (0) 12 minutes ago             unruffled_perlman
3a3b0777bdf9   96ebc284383f   "sleep 10"      29 minutes ago   Exited (0) 29 minutes ago             affectionate_wescoff
a09a4fcd27bf   96ebc284383f   "sleep 10"      30 minutes ago   Exited (0) 30 minutes ago             optimistic_wu
c01d8fd8d080   hello-world    "/hello"        44 minutes ago   Exited (0) 44 minutes ago             blissful_bohr
53d07f3cb5e3   hello-world    "/hello"        45 minutes ago   Exited (0) 45 minutes ago             elastic_bhabha
nagy_disappointed@Nagy:~/dockerLabs$ sudo docker container prune
WARNING! This will remove all stopped containers.
Are you sure you want to continue? [y/N] Y
Deleted Containers:
4c88f210d489a2698df05968d2c52e42940e97a844570aef9ba7b521a6a4b4a6
d0a61e5bfb9de0e566e1bcddb8680e97f046699eee4809e6bc0cc3524f77ab3e
3a3b0777bdf97cf484089f229d4c6c5970a98f19ed6aecb472f6cd2bc4429b5f
a09a4fcd27bf43e42b91e76f17943619fbb4221e4366d20c592710dbb589e2fe
c01d8fd8d080fcc2dca5367c3be8016d8b4e968c45aba497914a32ff44388708
53d07f3cb5e3796f7c114744eb320e116bcee460cbc5c2e9b604d94a0c4b910c

Total reclaimed space: 24B
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
nagy_disappointed@Nagy:~/dockerLabs$ touch hello.html
```
#### 2. Write Dockerfile and Copy the HTML file to the Docker Image
```bash
From nginx:1.23
COPY hello.html /usr/share/nginx/html/hello.html
```
#### 3. Run Container with New Image
```bash
sudo docker build -t html-server .
[+] Building 25.0s (7/7) FINISHED                                docker:default
 => [internal] load build definition from Dockerfile                       0.0s
 => => transferring dockerfile: 106B                                       0.0s
 => [internal] load .dockerignore                                          0.0s
 => => transferring context: 2B                                            0.0s
 => [internal] load metadata for docker.io/library/nginx:1.23              5.6s
 => [internal] load build context                                          0.0s
 => => transferring context: 49B                                           0.0s
 => [1/2] FROM docker.io/library/nginx:1.23@sha256:f5747a42e3adcb3168049  19.0s
 => => resolve docker.io/library/nginx:1.23@sha256:f5747a42e3adcb3168049d  0.0s
 => => sha256:f5747a42e3adcb3168049d63278d7251d91185bb511 1.86kB / 1.86kB  0.0s
 => => sha256:a97a153152fcd6410bdf4fb64f5622ecf97a753f07d 1.57kB / 1.57kB  0.0s
 => => sha256:a85095acb8962c7e1b8b45394a0fac9d37b704dbb117192 624B / 624B  0.3s
 => => sha256:a7be6198544f09a75b26e6376459b47c5b9972e7aa7 7.92kB / 7.92kB  0.0s
 => => sha256:f03b40093957615593f2ed142961afb6b540507e 31.40MB / 31.40MB  17.1s
 => => sha256:0972072e0e8a1dfea4404b5b1380f774ba845619 25.58MB / 25.58MB  15.7s
 => => sha256:d24b987aa74e1bc16eb176b252937c6ba7bd899f6dfbade 958B / 958B  1.1s
 => => sha256:6c1a86118ade98d785a80fd31c27eec32f6147ab9bbcda5 772B / 772B  2.0s
 => => sha256:9989f7b3322844aaf941b2867b2d611d07042c956a0 1.41kB / 1.41kB  3.0s
 => => extracting sha256:f03b40093957615593f2ed142961afb6b540507e0b47e3f7  1.1s
 => => extracting sha256:0972072e0e8a1dfea4404b5b1380f774ba8456190828e247  0.5s
 => => extracting sha256:a85095acb8962c7e1b8b45394a0fac9d37b704dbb1171925  0.0s
 => => extracting sha256:d24b987aa74e1bc16eb176b252937c6ba7bd899f6dfbade2  0.0s
 => => extracting sha256:6c1a86118ade98d785a80fd31c27eec32f6147ab9bbcda52  0.0s
 => => extracting sha256:9989f7b3322844aaf941b2867b2d611d07042c956a0f9548  0.0s
 => [2/2] COPY hello.html /usr/share/nginx/html/hello.html                 0.4s
 => exporting to image                                                     0.0s
 => => exporting layers                                                    0.0s
 => => writing image sha256:c0ffadc9ec1bb67be70e281987d29488fade43068960c  0.0s
 => => naming to docker.io/library/html-server               
```

#### 4. Test the Container, open your browser and navigate to http://localhost:8088 to check if everything is okay
```bash
sudo docker run -d -p 8080:80 html-server
5ac3ddc59110c0316f5b56acdf1798520daad86490896113a13e3974df7b7807

```

