# RED

* bridge: Es la red a la que por defecto se pueden conectar contenedores a traves de un key word "link". Esto ya esta en desuso.
* host: Es la forma que tiene docker, de representar a la red de la máquina. Se puede decirle a un contenedor que corra con la red en modo host, como si la red del contenedor sea la red de la computadora. Esto es peligroso y casi nunca deberiamos usarlo.
* none: Si a un contenedor corremos con esta network, es como desabilitar la red al contenedor, este no va poder recibir y enviar nada, va estar absolutamente aislado.

```shell
docker network ls
```

Creando nuestra porpia red

```shell
# --attachable Es para permitir que otros contenedores en el futuro se conecten a esta red
#docker network create --attachable nombre_red
docker network create --attachable platzinet

docker run -d --name db mongo
# Agredando a una red un contenedor
# Dentro de la red cada contenedor tiene su ip interna
# docker network connect nombre_red nombre_contenedor
docker network connect nombre_red nombre_contenedor

# Ver que contenedores estan conectados a la red
docker network inspect platzinet

# Agrgando variables de entorno
docker run -d --name app -p 3000:3000 --env MONGO_URL=mongodb://db:27017/test platziapp
docker network connect platzinet app
```

* Si dos contenedores estan conectados a la misma red utilizando como hosting el nombre del contenedor.

Eliminar una red

```shell
docker network rm platzinet
```

