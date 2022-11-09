# Docker Image vince-forty3/svn-server-ubuntu

## Description
This Docker image is based on **Ubuntu** with an Apache2 web-server and svn. The if.svnadmin web-interface is used to administrate svn. In addition to http:// the svn:// protocol can be used.The image can be used on ARM hardware (i.e. Raspberry Pi) and X86 hardware.

## Building the image
Build with
```
sudo docker build . -t vince-forty3/svn-server-ubuntu
```
### Build on Rapberry Pi with arm64 architecture
It might be necessary to install the RasPi Kernel headers for a successfull build.
```
sudo apt install raspberrypi-kernel-headers
sudo reboot
```

## Create a container from the image
To create a container with the repository data located on the host machine e.g. in the directory /data/docker/svn-server execute the following command:
```
docker run -d --name svn-server -p 80:80 -p 3960:3960 -v /data/docker/svn-server:/home/volumes/svn --restart unless-stopped vince-forty3/svn-server-ubuntu
```
Test if everything is up and running by opening a browser and open the url 'http://localhost/svn'. As you have not specified a user yet just ignore the username and password dialog.

## Docker Compose
A sample docker-compose.yml is attached in the files.
Note: A previous build is necessary. Currently the image is not provided over Docker Hub.

## Configuration
To create repositories and add users go to 'http://localhost/svnadmin/'. On the first start a username and password for the web admin interface has to be defined. 

## Fork
Fork of smezger/svn-server-ubuntu