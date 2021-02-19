---
layout: post
title: Imágenes y contenedores
categories: post
permalink: /Blog/Imágenes-y-contenedores/
---
## Imágenes

* Una imagen es una plantilla de solo lectura con instrucciones para crear un contenedor Docker.

* A menudo, una imagen se basa en otra imagen, con alguna personalización adicional. Por ejemplo, puede crear una imagen basada en la imagen de ubuntu, pero a su vez instalar el servidor web Apache y sus aplicaciones, así como los detalles de configuración necesarios para que su aplicación se ejecute.

* Puede crear sus propias imágenes o solo puede usar las creadas por otros publicadas en un registro.

* Para crear su propia imagen, cree un Dockerfile con una sintaxis simple para definir los pasos necesarios para crear la imagen y ejecutarla.

* Cada instrucción en un Dockerfile crea una capa en la imagen. Cuando cambia el Dockerfile y reconstruye la imagen, solo se reconstruyen las capas que han cambiado. Esto es parte de lo que hace que las imágenes sean tan livianas, pequeñas y rápidas, en comparación con otras tecnologías de virtualización.

## Contenedores

* Un contenedor es una instancia ejecutable de una imagen. Puede crear, iniciar, detener, mover o eliminar un contenedor utilizando Docker API o CLI. Puede conectar un contenedor a una o más redes, adjuntarle almacenamiento o incluso crear una nueva imagen en función de su estado actual.

* Por defecto, un contenedor está relativamente bien aislado de otros contenedores y su máquina host. Puede controlar cuán aislados están la red, el almacenamiento u otros subsistemas subyacentes de un contenedor de otros contenedores o de la máquina host.

* Un contenedor se define por su imagen, así como por las opciones de configuración que le proporcione cuando lo cree o lo inicie. Cuando se elimina un contenedor, cualquier cambio en su estado que no esté almacenado en un almacenamiento persistente desaparecerá.

## Contenedores - Comandos

* Obtener comandos del módulo contenedores

```
docker container --help
```

* Iniciar el contenedor hello-world

```
docker container run hello-world
```

## Eliminando imágenes y contenedores - Comandos

* Ayuda para eliminar contenedores

```
docker container rm --help
```

* Ayuda para eliminar imágenes

```
docker image rm --help
```

### Referencias

* Resumen de docker. Disponible en: [Docker overview](https://docs.docker.com/get-started/overview/)

## ISSUU

Puedes ver toda la información de esta sección del blog, en una diapositiva para que la compartas en tú salón de clase.

* [Imágenes y contenedores](https://issuu.com/johanse/docs/seccion-4-imagenes-y-contenedores.pptx)
