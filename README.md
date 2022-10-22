## 👋 Welcome to docker 🚀  

A self contained docker image with the ability to  
build docker images using the docker buildx command  
  
  
## Requires scripts to be installed  

```shell
 sudo bash -c "$(curl -q -LSsf "https://github.com/systemmgr/installer/raw/main/install.sh")"
 systemmgr --config && systemmgr install scripts  
```

## Automatic install/update  

```shell
dockermgr update docker
```

OR

```shell
mkdir -p "$HOME/.local/share/srv/docker/docker/dataDir"
git clone "https://github.com/dockermgr/docker" "$HOME/.local/share/CasjaysDev/dockermgr/docker"
cp -Rfva "$HOME/.local/share/CasjaysDev/dockermgr/docker/dataDir/." "$HOME/.local/share/srv/docker/docker/dataDir/"
```

## via command line  

```shell
docker pull casjaysdevdocker/docker:latest && \
docker run -d \
--restart always \
--privileged \
--name casjaysdevdocker-docker \
--hostname casjaysdev-docker \
-e TZ=${TIMEZONE:-America/New_York} \
-v $HOME/.local/share/srv/docker/docker/dataDir/data:/data:z \
-v $HOME/.local/share/srv/docker/docker/dataDir/config:/config:z \
-p 80:80 \
casjaysdevdocker/docker:latest
```

## Build image
  
You can leave registry empty if you are using docker hub.  
IF you want to build multiple images then set our folder names as your repo name  
and set the variable ORG to your username or org name.  
The TAG_NAME variable is the name of the image  
  
```shell
docker pull casjaysdevdocker/docker:latest && \
docker run -ti --rm \
--privileged \
--name casjaysdevdocker-buildx \
--hostname casjaysdev-docker \
-e ORG="" \
-e REGISTRY="" \
-e TAG_NAME="" \
-e TZ=${TIMEZONE:-America/New_York \
-v "$HOME/.docker/config.json":"/root/docker/.config.json" \
-v "$PWD":"/root/build" \
casjaysdevdocker/docker:latest buildx 
```

## via docker-compose  

```yaml
version: "2"
services:
  docker:
    image: casjaysdevdocker/docker
    container_name: docker
    environment:
      - TZ=America/New_York
      - HOSTNAME=casjaysdev-docker
    volumes:
      - $HOME/.local/share/srv/docker/docker/dataDir/data:/data:z
      - $HOME/.local/share/srv/docker/docker/dataDir/config:/config:z
    ports:
      - 80:80
    restart: always
```

## Author  

🤖 casjay: [Github](https://github.com/casjay) [Docker](https://hub.docker.com/r/casjay) 🤖  
📽  dockermgr: [Github](https://github.com/dockermgr) [Docker](https://hub.docker.com/r/dockermgr) 📽  
⛵ CasjaysDev Docker: [Github](https://github.com/casjaysdevdocker) [Docker](https://hub.docker.com/r/casjaysdevdocker) ⛵  
