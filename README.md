Docker Instalaltion Prod Way - 

Prerequisites-

1. Launch and Ec2 instance taking Ubuntu 22.04 OS 

Docker :

How to install Docker ?

Install Docker on Ubuntu : PROD

A. Set up the repository

1. Update the apt package index and install packages to allow apt to use a repository over HTTPS

sudo apt update -y


sudo apt-get install \
    ca-certificates \
    curl \
    gnupg \
    lsb-release
	
	
2. Add Docker’s official GPG key

sudo mkdir -p /etc/apt/keyrings

curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg


3. Use the following command to set up the repository

echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
  
  
B. Install Docker Engine 

Update the apt package index, and install the latest version of Docker Engine, containerd, and Docker Compose

sudo apt-get update

sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin


C. Verify that Docker is installed correctly by running the hello-world image 

sudo service docker start

sudo docker run hello-world (optional)

D. Verify the docker version with below command

docker version 

E. If you face socket related eprmission error execute below command 

sudo chmod 777 /var/run/docker.sock

F. Install docker on ubuntu with single line command : POC

sudo apt  install docker.io


Docker Practical 1 : Pull official Image from DockerHub & Run on your ubuntu instance

1. Using docker, pull the latest version of nginx

docker pull nginx

2. Verify that the image was pulled successfully

docker images

3. Run the container using the nginx image

docker run --name nginx -p 8080:80 -d nginx

4. Check the status of the Running container

docker ps

5. Verify connectivity to the nginx container through UI

< PUBLIC_IP_ADDRESS OF VM >:8080

6. access your docker container

docker exec -it < container name > /bin/sh

7. Update the webserver default page(Garbage Method)- Not recommended in Prod

cd /usr/share/nginx/html

ls -lrt

cat index.html

sed -i -e 's/nginx!/Cloudworld This is docker practical, I am your Intsrutcor/g' index.html

To avoid garbage method we use Docker File

8. Exit from Container

exit

9. Try to remove a container (It will give error)

docker rm container name/id

7. Stop the container

docker stop < container name >

8. To Verify Stop Container Status & the container has been removed

docker ps -a

9. Remove Images

docker rmi < image-id >


