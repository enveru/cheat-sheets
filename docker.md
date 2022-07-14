# Install Docker

## Installation Steps On Ubuntu

1.  Remove old versions of Docker.

        sudo apt-get remove docker docker-engine docker.io containerd runc

2.  Setup the repository.

        sudo apt-get update

        sudo apt-get install \
        ca-certificates \
         curl \
        gnupg \
        lsb-release

3.  Add Docker’s official GPG key.

        sudo mkdir -p /etc/apt/keyrings
        sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg

4.  Use the following command to set up the repository.

        echo \
        "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
        $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

5.  Install Docker engine and Docker Compose.

        sudo apt-get update
        sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin

## Pull Docker Images

Check for lates images on Docker Hub.

1.  Redis

        docker pull redis:7.0.0-alpine3.16

2.  RabbitMQ

        docker pull rabbitmq:3.10.5-management

3.  Node JS

        docker pull node:18.4.0-alpine3.16

4.  Nginx

        docker pull nginx:1.21.6-alpine

5.  Certbot

        docker pull certbot/certbot

6.  Ubuntu

        docker pull ubuntu:focal-20220316
