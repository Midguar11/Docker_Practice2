# Create Docker lab with bento/ubuntu-21.10 (Use Vagrant)

    vagrant up
    vagrant ssh dock1
    sudo cp /vagrant/hosts_file /etc/hosts
    cat /etc/hosts
    
# Update

    sudo apt update
    sudo apt dist-upgrade -y

# reboot dock1, install docker

    sudo apt install docker.io -y

# Docker status

    systemctl status docker
    sudo systemctl enable docker
    sudo systemctl start docker
    systemctl status docker

# Run docker

    sudo docker run hello-world
    sudo usermod -aG docker vagrant

# reboot dock1, search images and pull ubuntu

    docker run hello-world
    docker images
    docker search ubuntu
    docker pull ubuntu
    docker images
    docker run ubuntu
    docker run nginx
   # <"ctrl +c">
    docker ps
    docker ps -a

# Connect Conainer

    docker run -it ubuntu /bin/bash
    apt update && apt install vim-nox -y
    vim

# fix Conainter

    docker run -it -d ubuntu
    docker ps
    docker attach <conainter id>
    docker run -it ubuntu /bin/bash
    apt update && apt install vim-nox -y
   # <left ctrl +p +q>
   
# New Docker "nginx" and open port

    docker run nginx
    docker run -it -d -p 8080:80 nginx
    ip a
 # cheking nginx pastle in browser eth1: ip xxxx.xxx.xxx.xxx:8080
    docker stop 1bf
    docker run -it -d --restart unless-stopped -p 8080:80 nginx
    docker attach <conainter id>
   # <left ctrl +p +q>
    docker ps

# Modified docker images

    docker run -it ubuntu
    apt update & apt dist-upgrade -y
    apt install apache2 -y
    /etc/init.d/apache2 status
    /etc/init.d/apache2 start
   # <left ctrl +p +q>
    docker commit <conainter id> ubuntu:apache2
    docker images
    docker ps
    docker stop <runing conainter id>
    docker ps
    docker run -it -d -p 8080:80 ubuntu:apache2
   # cheking nginx pastle in browser eth1: ip xxxx.xxx.xxx.xxx:8080
   # doesn't work, it is need entry point
    docker commit --change='ENTRYPOINT ["apachectl", "-DFOREGROUND"]' <<conainter id>> ubuntu_apache2:ver1.1
   # stop all container
    docker stop <<runing conainter id>>
    docker run -it -d -p 8080:80 ubuntu_apache2:ver1.1
    docker stop <<runing conainter id>>

   # Use dockerfile to build images
  
    mkdir dockerfile
    cd dockerfiles/
    nano Dockerfile
    docker build -t ubuntu_apache2:ver1.2 .
    docker run -it -d -p 8080:80 ubuntu_apache2:ver1.2



   
     

