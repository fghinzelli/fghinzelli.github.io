# Comandos Docker

## Informações gerais 

`docker version` - exibe a versão do docker que está instalada.

`docker inspect ID_CONTAINER` - retorna diversas informações sobre o container.

`docker ps` - exibe todos os containers em execução no momento.

`docker ps -a` - exibe todos os containers, independente de estarem em execução ou não.

## Execução de containers

`docker run NOME_DA_IMAGEM` - cria um container com a respectiva imagem passada como parâmetro.

`docker run -it NOME_DA_IMAGEM` - conecta o terminal que estamos utilizando com o do container.

`docker run -d -P --name NOME dockersamples/static-site` - ao executar, dá um nome ao container.

`docker run -d -p 12345:80 dockersamples/static-site` - define uma porta específica para ser atribuída à porta 80 do container, neste caso 12345.

`docker run -d -e AUTHOR="Fulano" dockersamples/static-site` - a opção `-e` especifica uma variável de ambiente a ser utilizada no container

`docker run -v "CAMINHO_VOLUME" NOME_DA_IMAGEM` - cria um volume no respectivo caminho do container.

`docker run -it --name NOME_CONTAINER --network NOME_DA_REDE NOME_IMAGEM` - cria um container especificando seu nome e qual rede deverá ser usada.

## Inicialização/interrupção de um container já existente

`docker start ID_CONTAINER` - inicia o container com id em questão. 

`docker start -a -i ID_CONTAINER` - inicia o container com id em questão e integra os terminais, além de permitir interação entre ambos.

`docker stop ID_CONTAINER` - interrompe o container com id em questão.

## Remoção de containers e imagens

`docker rm ID_CONTAINER` - remove o container com id em questão.

`docker container prune` - remove todos os containers que estão parados.

`docker rmi NOME_DA_IMAGEM`- remove a imagem passada como parâmetro.

## Construção de Dockerfile

`docker build -f Dockerfile . ` - cria uma imagem a partir de um Dockerfile.

`docker build -f Dockerfile -t NOME_USUARIO/NOME_IMAGEM . `- constrói e nomeia uma imagem não-oficial.

`docker build -f Dockerfile -t NOME_USUARIO/NOME_IMAGEM CAMINHO_DOCKERFILE . `- constrói e nomeia uma imagem não-oficial informando o caminho para o Dockerfile.

## Docker Hub - Enviar e Buscar imagens

`docker login` - inicia o processo de login no Docker Hub.

`docker push NOME_USUARIO/NOME_IMAGEM` - envia a imagem criada para o Docker Hub.

`docker pull NOME_USUARIO/NOME_IMAGEM` - baixa a imagem desejada do Docker Hub.

## Rede

`hostname -i` - mostra o ip atribuído ao container pelo docker (funciona apenas dentro do container). 

`docker network create --driver bridge NOME_DA_REDE` - cria uma rede especificando o driver desejado.

`docker run --name MEU-CONTAINER --network NOME_DA_REDE NOME_IMAGEM` - Inicia um container na rede criada.

## Docker file  
~~~~
FROM node:latest  
MAINTAINER Fernando Ghinzelli  
ENV PORT=3000  
COPY . /var/www  
WORKDIR /var/www  
RUN npm install  
ENTRYPOINT npm start  
EXPOSE $PORT  
~~~~

## Docker Compose
~~~~
version: '3'
services:
    nginx:
        build:
            dockerfile: ./docker/nginx.dockerfile
            context: .
        image: nginx
        container_name: nginx
        ports:
            - "80:80"
        networks: 
            - production-network
        depends_on: 
            - "node1"
            - "node2"
            - "node3"

    mongodb:
        image: mongo
        networks: 
            - production-network

    node:
        build:
            dockerfile: ./docker/alura-books.dockerfile
            context: .
        image: douglasq/alura-books
        container_name: alura-books-1
        ports:
            - "3000"
        networks: 
            - production-network
        depends_on:
            - "mongodb"
networks: 
    production-network:
        driver: bridge
~~~~

## Logs

`docker logs <container-id>`
