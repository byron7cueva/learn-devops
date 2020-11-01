# Docker compose

* Es una herramiente que viene integrada en docker desktop, pero no viene instalado con linux.
* Nos permite describir de forma declarativa la arquitectura de nuestra aplicación.
* Un dockerfile es una descripción imperativa es decirle paso a paso que quiero que haga y como quiero que construya la imagen.
* Nos permite escalar un servicio, tener mas contenedores en un servicio.
* Utiliza el docker-compose.yml file y utiliza la sintaxis YAML.
* Al correr los contenedores los va nombrar de la siguiente manera.
  * directorioActual_nombreServicio_1
* Al crear los networks se nombran de la siguiente manera:
  * directorioActual_default
  * default: Porque es el network default que siempre crea docker-compose para los contenedores que se encuentren en el docker-compose.yml

```shell
# Levantar los servicios indicados en docker-compose.yml
docker-compose up

# --detach
docker-compose up -d

# Nos dice que comandos estan ejecutandoce
docker-compose ps

# Ver los logs
# docker-compose logs nombre_servicio
docker-compose logs app
# Ver los logs haciendo follow
docker-compose logs -f app

# Meterce a un contenedor
# docker-compose exec nombre_servicio comando
docker-compose exec app bash

# Eliminar
# Todos los servicios
# Todos los contenedores
# Network
# Y el estado queda completamente limpio
# Si aveces algo falla podemos regenerar todo desde cero.
docker-compose down

# Construir la imagen
docker-compose build
# Correr los contenedores a partir de la imagen que contruimos
# Si se corre antes de contruir doker compose va hacer el build primero por si solo
docker-compose up -d

# Escalando un servicio a un número de container
# Pero puede dar problemas entre los puertos
docker-compose scale app=4

# Ver todos los logs de todos los contenedores ese servicio
# Los difrencia con colores
docker-compose scale app=4
```

