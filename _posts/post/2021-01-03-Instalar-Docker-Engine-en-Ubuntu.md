---
layout: post
title: Instalar Docker Engine en Ubuntu
categories: post
permalink: /Blog/Instalar-Docker-Engine-en-Ubuntu/
---
## 1. Realizar una actualización.
```
sudo apt-get update
```

## 2. Instale paquetes para permitir el uso de un repositorio sobre HTTPS.

```
sudo apt-get install \
apt-transport-https \
ca-certificates \
curl \
gnupg-agent \
software-properties-common
```

## 3. Agregue la clave GPG oficial de Docker.

```
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
```

## 4. Agregar los repositorios estables de Docker.

```
sudo add-apt-repository \
"deb [arch=amd64] https://download.docker.com/linux/ubuntu \
$(lsb_release -cs) \ stable"
```

## 5. Actualizar los paquetes relacionados con los repositorios del sistema.

```
sudo apt-get update
```

## 6. Instalar la versión para la comunidad, conocido como Docker CE.

```
sudo apt-get install docker-ce docker-ce-cli containerd.io
```
## Verificar instalación de Docker

* Usar el siguiente comando:

```
docker --version
```

* Obteniendo información de la instalación en el sistema.

```
docker info
```

## Agregar el usuario al grupo de Docker

* Usar el siguiente comando:

```
sudo usermod -aG docker ubuntu
```

## Primer contenedor

* Usar el siguiente comando:

```
docker container run hello-world
```

<br>
<img class="img-center" src="{{ site.baseurl }}/images/instalar-docker-engine-en-ubuntu/primer-contenedor.png" title="Primer contenedor" name="Primer contenedor"/>
<br>

### Referencias

* Instalar Docker Engine en Ubuntu. Disponible en: [Install Docker Engine on Ubuntu](https://docs.docker.com/engine/install/ubuntu/)

## ISSUU

Puedes ver toda la información de esta sección del blog, en una diapositiva para que la compartas en tú salón de clase.

* [Instalar Docker Engine en Ubuntu](https://issuu.com/johanse/docs/seccion-2-instalacion-de-docker.pptx)

## VIDEO

{% include youtube.html id='3p-6Zi6g_jc' %}

<br>

## VIDEO

{% include youtube.html id='fhU8JIKq9LU' %}

<br>
