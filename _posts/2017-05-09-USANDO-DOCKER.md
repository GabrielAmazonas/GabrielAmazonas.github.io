---
layout: post
title: Docker - Um guia rápido
---


## Download do Docker: https://www.docker.com/products/docker-toolbox

### Comandos e Conceitos Básicos:

- `docker pull nomeDaImagem` Faz o download da imagem referida para a plataforma docker.

- `docker images` Lista as imagens disponíveis na plataforma

 -`docker run aliasDoContainer comandoNoContainer` Irá executar o comando no container especificado.
 
 -`docker run --name nomeDoContainer `
 
 -`docker ps -a` Listará todos os containers
 
 - `docker stop $(docker ps -aq)`
 
 
