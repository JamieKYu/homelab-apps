
# homelab-apps

This project is a set of useful Docker containers that I self-hosted in my home lab.  It contains docker-compose YAML that can be used to deploy the containers.


## Pre-requisite Installations

Make sure you have installed Docker and docker-compose.

```bash
  sudo apt-get update && sudo apt-get upgrade
  curl -sSL https://get.docker.com | sh
  sudo usermod -aG docker ${USER} && groups ${USER}
  sudo apt-get install libffi-dev libssl-dev
  sudo apt-get install -y python3 python3-pip
  sudo apt-get install rustc
  sudo pip3 install setuptools_rust docker-compose
  sudo systemctl enable docker
```

## Run Locally

Clone the project

```bash
  git clone https://github.com/JamieKYu/homelab-apps
```

Go to the project directory

```bash
  cd homelab-apps
```

For the desired application you want to deploy and run go to the directory (ie Portainer) and create a .env file

```bash
  cd portainer
  nano .env
```

Paste the following lines with environment variables/values and save/exit.  Example with Portainer:

```bash
  PORT_ADMIN=9000
  VOLUME_ROOT=~
  LABEL_WATCHTOWER_ENABLE=false
```

Output the docker compose configuration

```bash
  docker-compose --env-file .env config
```

Deploy and run the container

```bash
  docker-compose --env-file .env up -d
```

Check to see that your container is running successfully

```bash
  docker ps
```
