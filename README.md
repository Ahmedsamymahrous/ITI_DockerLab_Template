# ITI - Docker Lab2 🐋

## Task 1:
Run a container using nginx image, and mount a directory from your host into the 
Docker container. example: /home/samy/nginx:/home/nginx (bind mount)
```bash
# New Directory
mkdir nginxBindMount
cd nginxBindMount

# Create A Container Via Bind Mount
docker run -d --name nginxBindMount -v /root/nginxBindMount:/user/share/nginx/html nginx:1.23 .
docker exec -it nginxBindMount /bin/bash

```
---

## Task 2:
### Steps
#### 1. Create 2 docker network (net-1 & net-2)
```bash
docker network create network_1
docker network create network_2
```
#### 2. Run 2 new containers using nginx:alpine image, and attach the net-1 to them
```bash
docker run -d --name nginx_net1 --net network_1 nginx:alpine
docker run -d --name nginx_net2 --network network_1 nginx:alpine
```
#### 3.  Run another 1 new containers using nginx:alpine image, and attach the net-2 to them
```bash
docker run -d --name nginx_net3 --net network_2 nginx:alpine
```
#### 4. Inspect the 3 containers to know their IPs and write them aside
```bash
docker inspect -f '{{.NetworkSettings.Networks.network_1.IPAddress}}' nginx_net1
172.18.0.2

docker inspect -f '{{.NetworkSettings.Networks.network_1.IPAddress}}' nginx_net2
172.18.0.3

docker inspect -f '{{.NetworkSettings.Networks.network_2.IPAddress}}' nginx_net3
172.20.0.2
can use : docker inspect nginx_net1 | grep IPAddress
```
#### 5. Enter a container in the net-1 network and try to ping a container in the net-2 
network (What do you notice?)
```bash
docker exec -it nginx_net1 sh 
Use ping or curl
ping 172.20.0.2
```
* Note: Ping Failed Because Both Networks Are in a different networks

#### 6. Enter a container in the net-1 network and try to ping the other container in the 
same network (What do you notice?)
```bash
docker exec -it nginx_net1 sh 
curl 172.18.0.2
ping 172.18.0.3
```
* Notice: Ping Run Successfully Because Two Containers are in the same network
---
## Task 3: Explain the difference between Docker volumes and Bind Mount.
### Bind Mount 
- Allows you to Add Driectory in your virtual machine into your Created Container
### Volume 
- Allows you to Save the files within your virtual machine so if the container was Removed your files will be remained

