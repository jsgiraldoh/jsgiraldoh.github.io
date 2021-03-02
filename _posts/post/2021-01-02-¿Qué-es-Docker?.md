---
layout: post
title: ¿Qué es Docker?
categories: post
permalink: /Blog/Qué-es-Docker/
---
* Docker es una plataforma abierta para desarrollar, enviar y ejecutar aplicaciones. Docker le permite separar sus aplicaciones de su infraestructura para que pueda entregar el software rápidamente. Con Docker, puede administrar su infraestructura de la misma manera que administra sus aplicaciones. Al aprovechar las metodologías de Docker para enviar, probar e implementar código rápidamente, puede reducir significativamente el retraso entre escribir código y ejecutarlo en producción.

* Docker ofrece la capacidad de empaquetar y ejecutar una aplicación en un entorno aislado llamado contenedor. El aislamiento y la seguridad le permiten ejecutar muchos contenedores simultáneamente en un host determinado.

* Los contenedores son livianos porque no necesitan la carga adicional de un hipervisor, sino que se ejecutan directamente dentro del núcleo de la máquina host.

* Esto significa que puede ejecutar más contenedores en una combinación de hardware determinada que si estuviera utilizando máquinas virtuales. ¡Incluso puede ejecutar contenedores Docker dentro de máquinas host que en realidad son máquinas virtuales!

## ¿Para qué puedo usar Docker?

## Entrega rápida y consistente de sus aplicaciones

* Docker optimiza el ciclo de vida del desarrollo al permitir que los desarrolladores trabajen en entornos estandarizados utilizando contenedores locales que proporcionan sus aplicaciones y servicios. Los contenedores son excelentes para la integración continua y los flujos de trabajo de entrega continua (CI / CD).

## Considere el siguiente escenario de ejemplo:

* Sus desarrolladores escriben código localmente y comparten su trabajo con sus colegas utilizando contenedores Docker.

* Usan Docker para llevar sus aplicaciones a un entorno de prueba y ejecutar pruebas automáticas y manuales.

* Cuando los desarrolladores encuentran errores, pueden corregirlos en el entorno de desarrollo y volver a implementarlos en el entorno de prueba para pruebas y validación.

* Cuando se completa la prueba, obtener la solución para el cliente es tan simple como llevar la imagen actualizada al entorno de producción.

## Productos y herramientas

<div class="home-images">
	<div class="home-images">
		<img src="{{ site.baseurl }}/images/prod-docker/docker.png" title="Docker" name="Docker" />
		<img src="{{ site.baseurl }}/images/prod-docker/docker-compose.png" title="Docker-compose" name="Docker-compose" />
		<img src="{{ site.baseurl }}/images/prod-docker/docker-registry.png" title="Docker-registry" name="Docker-registry" />
	</div>
	<div class="home-images">
		<img src="{{ site.baseurl }}/images/prod-docker/docker-swarm.png" title="Docker-swarm" name="Docker-swarm" />
		<img src="{{ site.baseurl }}/images/prod-docker/docker-machine.png" title="Docker-machine" name="Docker-machine" />
	</div>
</div>

## Video

{% include youtube.html id='UuZl1iKK14E' %}

### Referencias

* Resumen de docker. Disponible en: [Docker overview](https://docs.docker.com/get-started/overview/)

## ISSUU

Puedes ver toda la información de esta sección del blog, en una diapositiva para que la compartas en tú salón de clase.

* [Qué es Docker](https://issuu.com/johanse/docs/seccion-1-que-es-docker.pptx)
