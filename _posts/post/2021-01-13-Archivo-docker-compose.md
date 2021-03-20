---
layout: post
title: Archivo docker-compose
categories: post
permalink: /Blog/Archivo-docker-compose
---
Crear la carpeta para el proyecto

```
mkdir proxy
```

Crear y editar el archivo Compose

```
vim docker-compose.yml
```

```
version: '3'
services:
  web:
    image: dockercloud/hello-world
  lb:
    image: dockercloud/haproxy
    links:
      - web
    volumes:
      - /var/run/docker.sock:/var/run/docker.sock
    ports:
      - 80:80
```

Utilizar los siguientes comandos:

```
docker-compose up -d
```

```
docker-compose ps
```

### Referencias

* Disponible en: [Integrando docker a su infraestructura y servicios](https://mmorejon.io/curso/integrando-docker-a-su-infaestructura-y-servicios)

## ISSUU

Puedes ver toda la información de esta sección del blog, en una diapositiva para que la compartas en tú salón de clase.

* [Archivo docker-compose](https://issuu.com/johanse/docs/seccion-12-archivo-docker-compose.pptx)

## Video

{% include youtube.html id='HhhFpa4ZrpA' %}
