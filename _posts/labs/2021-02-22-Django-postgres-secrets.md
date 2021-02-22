---
layout: post
title: Django-postgres-secrets-Parte-2
categories: labs
permalink: /Blog/Django-postgres-secrets/
---
# Sobre secretos

En términos de los servicios de Docker Swarm, un secreto es una masa de datos, como una contraseña, una clave privada SSH, un certificado SSL u otro dato que no debe transmitirse a través de una red o almacenarse sin cifrar en un Dockerfile o en el de su aplicación. código fuente. Puede usar los secretos de Docker para administrar de forma centralizada estos datos y transmitirlos de forma segura solo a aquellos contenedores que necesitan acceder a ellos. Los secretos se cifran durante el tránsito y en reposo en un Docker Swarm. Un secreto determinado solo es accesible para aquellos servicios a los que se les ha otorgado acceso explícito a él, y solo mientras esas tareas de servicio están en ejecución.

Puede usar secretos para administrar los datos confidenciales que un contenedor necesita en tiempo de ejecución, pero no desea almacenarlos en la imagen o en el control de fuente, como:

* Nombres de usuario y contraseñas
* Certificados y claves TLS
* Claves SSH
* Otros datos importantes como el nombre de una base de datos o servidor interno
* Cadenas genéricas o contenido binario (hasta 500 kb de tamaño)

Otro caso de uso para usar secretos es proporcionar una capa de abstracción entre el contenedor y un conjunto de credenciales. Considere un escenario en el que tiene entornos de desarrollo, prueba y producción separados para su aplicación. Cada uno de estos entornos puede tener diferentes credenciales, almacenadas en los Swarm de desarrollo, prueba y producción con el mismo nombre secreto. Sus contenedores solo necesitan saber el nombre del secreto para funcionar en los tres entornos.

# Cómo administra Docker los secretos

Cuando agrega un secreto al enjambre, Docker envía el secreto al administrador del enjambre a través de una conexión TLS mutua. El secreto se almacena en el registro de Raft, que está encriptado. Todo el registro de Raft se replica en los demás administradores, lo que garantiza las mismas garantías de alta disponibilidad para los secretos que para el resto de los datos de administración de enjambres.

Cuando concede acceso a un secreto a un servicio recién creado o en ejecución, el secreto descifrado se monta en el contenedor en un sistema de archivos en memoria. La ubicación del punto de montaje dentro del contenedor está predeterminada ```/run/secrets/<secret_name>``` en contenedores de Linux o ```C:\ProgramData\Docker\secrets``` en contenedores de Windows. También puede especificar una ubicación personalizada.

# Docker Secrets

Como podemos observar en el archivo Compose, configuramos la ```db``` contraseña en texto plano. Para evitar esto, podemos aprovechar los secretos de la ventana acoplable para almacenar la contraseña y compartirla de forma segura con los servicios que la necesiten. Podemos definir secretos y hacer referencia a ellos en los servicios como se muestra a continuación. La contraseña se almacena localmente en el ```project/db/password.txt``` archivo y se monta en los contenedores debajo ```/run/secrets/<secret-name>```.

```dockerfile=
version: "3"

services:
  db:
    image: postgres
    secrets:
      - db-password
    environment:
      - POSTGRES_DB=postgres
      - POSTGRES_USER=postgres
      - POSTGRES_PASSWORD_FILE=/run/secrets/db-password
  web:
    build: .
    command: python manage.py runserver 0.0.0.0:8000
    volumes:
      - .:/code
    ports:
      - "8000:8000"
    depends_on:
      - db

secrets:
  db-password:
    file: db/password.txt
```

[Aquí](https://github.com/jsgiraldoh/Django-postgres-secrets.git) se puede encontrar una aplicación de ejemplo que ejercita todos los aspectos que se discutieron.

# Verificando el despliegue

En este punto, su aplicación Django debería estar ejecutándose en el puerto 8000 de su host Docker. En Docker Desktop para Mac y Docker Desktop para Windows, vaya a http://localhost:8000 en un navegador web para ver la página de bienvenida de Django.

<img src="{{ site.baseurl }}/images/img-django-postgres/django.png" title="django" name="django"/><br>

Luego para verificar que la base de datos postgres, quedo bien configurada en el proyecto debemos dirigirnos al siguiente enlace, http://localhost:8000/admin. Esto nos debera mostrar la siguiente salida.

<img src="{{ site.baseurl }}/images/img-django-postgres-secrets/admin.png" title="admin" name="admin"/><br>

Si presenta algún incoveniente o error, debera ejecutar el siguiente comando; para que los scripts de administración preparen todos los elementos necesarios(tablas, sessiones, autorizaciones, etc) para su correcto funcionamiento.

```
docker-compose run web python manage.py migrate
````

Recuerde ejecutar este comando en el espacio de trabajo donde tienen los archivos necesarios para su correcta ejecución, si no lo recuerda en este punto, [Aqui](https://jsgiraldoh.github.io/Blog/Django-postgres/) esta el enlace para que recuerde el proceso de la primera parte de este tutorial.

Obtendrá una salida parecida a la siguiente **imagen**.

<img src="{{ site.baseurl }}/images/img-django-postgres-secrets/migrate.png" title="migrate" name="migrate"/><br>

Luego de que tenga todos los elementos listos, podra crear el super usuario, el cual le permitira acceder a la parte administrativa.

```
docker-compose run web python manage.py createsuperuser
```

<img src="{{ site.baseurl }}/images/img-django-postgres-secrets/superuser.png" title="superuser" name="superuser"/><br>

Para este ejemplo, se uso como usuario **root** y contraseña **root**, el correo electronico tiene validaciones así que debe estar bien escrito.

Por ultimo podra ingresar al portar con su usuario y contraseña y podra asegurarse de que todo quedo bien configurado.

<img src="{{ site.baseurl }}/images/img-django-postgres-secrets/view-users.png" title="view-users" name="view-users"/><br>

# Referencias

https://docs.docker.com/engine/swarm/secrets/#how-docker-manages-secrets

https://docs.docker.com/engine/swarm/secrets/#build-support-for-docker-secrets-into-your-images

https://www.docker.com/blog/containerized-python-development-part-2/

https://github.com/aiordache

https://docs.docker.com/compose/django/#more-compose-documentation

https://hub.docker.com/_/postgres

https://kubernetes.io/es/docs/concepts/configuration/secret/

https://mmorejon.io/blog/iniciar-proyecto-en-django-con-docker/
