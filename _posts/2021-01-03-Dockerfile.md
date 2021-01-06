---
layout: post
title: Dockerfile
permalink: /Blog/Dockerfile
---
<br>
<img class="img-center" src="{{ site.baseurl }}/images/dockerfile/dockerfile.png" title="Dockerfile" name="Dockerfile"/>
<br>

## Introducción a Dockerfile

* Docker construye las imágenes al leer las instrucciones que se encuentran en el fichero dockerfile.

* Dockerfile es el nombre de un documento de texto que contiene todos los comandos necesarios para poder crear imágenes (Dependencias, Programas, Código fuente, Configuraciones).

## Construir la primera imagen

* Primero se debe crear un directorio para el proyecto y después un archivo llamado Dockerfile.

* Luego se edita el archivo Dockerfile con un editor de texto.

* **FROM:** Es una etiqueta que le indica a Docker durante la construcción que se va a partir desde un lugar en especifico, en este caso, desde la imagen base ubuntu:16.04.

* **ENTRYPOINT:** Permite configurar el contenedor para que sea iniciado como un ejecutable.

<br>
<img class="img-center" src="{{ site.baseurl }}/images/dockerfile/primera-imagen.png" title="Primera-imagen" name="Primera-imagen"/>
<br>

* Utilizar el siguiente comando:

```
docker image build  --tag ejemplo .
```
<br>
<img class="img-center" src="{{ site.baseurl }}/images/dockerfile/build-image.png" title="Build-image" name="Build-image"/>
<br>

* Utilizar el siguiente comando:

```
docker image ls
```

<br>
<img class="img-center" src="{{ site.baseurl }}/images/dockerfile/image-ls.png" title="Build-image" name="Build-image"/>
<br>

* Utilizar el siguiente comando:

```
docker container run ejemplo
```

<br>
<img class="img-center" src="{{ site.baseurl }}/images/dockerfile/run-ejemplo.png" title="Build-image" name="Build-image"/>
<br>

# Construir la primera imagen - Comandos

* Utilizar el siguiente comando:

```
docker image history --help
```

Permite conocer de una imagen el conjunto de instrucciones que fueron ejecutadas para su construcción.

# Instrucciones en Dockerfile

* **LABEL:** Esta etiqueta es la encargada de agregar los metadatos a nuestra imagen; utilizando (llave, valor).

* **COPY:** Copiar ficheros o directorios desde la máquina hacia la estructura de ficheros de la imagen que se está creando.

### Referencias

* Referencia de Dockerfile. Disponible en: [Dockerfile reference](https://docs.docker.com/engine/reference/builder/)

* Hola docker. Disponible en: [Hola docker](https://lemoncode.net/lemoncode-blog/2019/11/5/hola-docker)

## ISSUU

Puedes ver toda la información de esta sección del blog, en una diapositiva para que la compartas en tú salón de clase.

* [Dockerfile](https://issuu.com/johanse/docs/seccion-5-dockerfile.pptx)
