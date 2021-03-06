
# For using it you do 

This command is for ubuntu if you are having permissions errors so with this CMD you will "acting as a root"
```
sudo -i
```

## install docker on ubuntu 

```
sudo apt-get install docker.io -y
```

##  Add this for docker interface network start to using it for apache
```
sudo echo 'auto docker0
iface docker0 inet static
      address 192.168.10.102
      netmask 255.255.255.0' >> /etc/network/interfaces
```

## Put the interface up for docker
```
sudo ifup docker0
```


# Info about how to use this container

* Just pull the container from this repo

``` 
docker pull caliari/ubuntu-apache 
```

* The the image name and the image ID

``` 
sudo docker images 
```

* Grab the image ID from this repo "caliari/ubuntu-apache"  and replace the imageID

``` 
sudo docker run --net=host -d -t imageID 
```

* ##### To check if the apache2 is running correctly just go to you browser

http://development.local

================== END ===============


## If you want to create a new git repository from the command line

```
sudo -i 
echo "# simple-docker-apache" >> README.md
git init
git add README.md
git commit -m "first commit"
git remote add origin https://github.com/Calliari/simple-docker-apache.git
git push -u origin master
```

## If you want to create a new docker repository from the command line

### First creata a dockerfile

```
touch Dockerfile
```

### Edit the 'Dockerfile' with vim or nano:

```
vim Dockerfile
```

### In the dockerfile just use the commands to config the docker container 

```
#Download base image ubuntu 16.04
FROM ubuntu:16.04

# Update repos
RUN apt-get update
RUN apt-get install -y apache2 nano curl

# Set apache2 ro start on boot
RUN echo 'service apache2 start' >> /etc/bash.bashrc

# Populate the apache html dictory with the index.html file with hello world
ADD index.html /var/www/html/
```

### Save the file and exit.
```
2 X esc + : + wq + enter
```

### Build New Docker Image and Create New Container Based on it

```
docker build -t apache-docker .
```

### When the command completed successfully, we can check the new image 'apache-docker' with the docker command below:

```
sudo docker images
```
### Pushing your image through the command line (cli)

```
docker commit fd0a57808308 caliari/apache-docker 
```

### Push the docker to the docker hub

```
docker login

```

```
sudo docker tag my_image DOCKER_ID_USER/my_image
```

```
sudo docker push DOCKER_ID_USER/my_image
sudo docker push caliari/apache-testing
```

### your docker image will start to upload the docker image in the docker hub
