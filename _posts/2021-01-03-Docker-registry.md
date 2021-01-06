---
layout: post
title: Docker Registry
permalink: /Blog/Docker-Registry
---
## ¿Qué es Docker Registry?

* El Docker registry es una aplicación del lado del servidor sin estado y altamente escalable que almacena y le permite distribuir imágenes de Docker.

**¿Por qué usarlo?**

Debe usar el Registry si desea:

  * Controlar estrictamente dónde se almacenan sus imágenes.

  * Poseer completamente su canal de distribución de imágenes.

  * Integre el almacenamiento y la distribución de imágenes en su flujo de trabajo de desarrollo interno.

## Alternativas

* Se recomienda a los usuarios que buscan una solución lista para usar que no requiera mantenimiento, que se dirijan al Docker Hub, que proporciona un registro alojado de uso gratuito, además de características adicionales (cuentas de la organización, compilaciones automatizadas y más).

## Comandos básicos

Corra un contenedor con la imagen de registry

```
docker run -d -p 5000:5000 --name registry registry:2
```

Extraiga (o cree) alguna imagen de Docker hub

```
docker pull ubuntu
```

Etiquete la imagen para que apunte a su registry

```
docker image tag ubuntu localhost:5000/myfirstimage
```

Envíelo al contendor registry

```
docker push localhost:5000/myfirstimage
```  

Descárguelo del contenedor registry

```
docker pull localhost:5000/myfirstimage
```

### Referencias

* Registro docker. Disponible en: [Registro docker](https://docs.docker.com/registry/)

## ISSUU

Puedes ver toda la información de esta sección del blog, en una diapositiva para que la compartas en tú salón de clase.

* [Docker Registry](https://issuu.com/johanse/docs/seccion-14-docker-registry.pptx)
