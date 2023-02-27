# dind

```sh
docker build -t sample-dind:latest .

docker network create sample-network
docker volume create sample-docker-certs-ca
docker volume create sample-docker-certs-client
# docker run -it --privileged --rm --network sample-network --network-alias docker -e DOCKER_TLS_CERTDIR=/certs -v sample-docker-certs-ca:/certs/ca -v sample-docker-certs-client:/certs/client sample-dind sh

# sample
docker run --privileged --name sample-docker -d --network sample-network --network-alias docker -e DOCKER_TLS_CERTDIR=/certs -v sample-docker-certs-ca:/certs/ca -v sample-docker-certs-client:/certs/client docker:dind
# docker run -it --rm --privileged --name sample-docker --network sample-network --network-alias docker -e DOCKER_TLS_CERTDIR=/certs -v sample-docker-certs-ca:/certs/ca -v sample-docker-certs-client:/certs/client docker:dind
docker run --rm --network sample-network -e DOCKER_TLS_CERTDIR=/certs -v sample-docker-certs-client:/certs/client:ro docker:latest version
docker run -it --rm --network sample-network -e DOCKER_TLS_CERTDIR=/certs -v sample-docker-certs-client:/certs/client:ro docker:latest sh
/ # docker version
/ # docker info
/ # docker run -it --rm bash
bash-5.2# ls
```