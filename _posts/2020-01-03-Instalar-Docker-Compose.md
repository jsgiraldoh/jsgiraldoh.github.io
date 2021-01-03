---
layout: post
title: Instalar Docker Compose
permalink: /Blog/Instalar-Docker-Compose/
---
1. Ejecute este comando para descargar la versión estable actual de Docker Compose:

```
sudo curl –L "https://github.com/docker/compose/releases/download/1.25.5/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
```

2. Aplique permisos ejecutables al binario

```
sudo chmod +x /usr/local/bin/docker-compose
```

3. Probar la instalación

```
docker-compose --version
```

### Referencias

* Instalar docker compose. Disponible en: [Instalar docker compose](https://docs.docker.com/compose/install/)

## ISSUU

Puedes ver toda la información de esta sección del blog, en una diapositiva para que la compartas en tú salón de clase.

* [Instalar Docker Compose](https://issuu.com/johanse/docs/seccion-11-instalar-docker-compose.pptx)
