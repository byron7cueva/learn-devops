## Multi Stage Builds

* Nos permite utilizar dockerfiles que tienen varias faces de build. Una fase puede utilizar el output de la otra, de tal manera que podemos hacer en una parte build de test y otra solo que queramos las cosas que se queden en produccion.

```shell
# -f Indicar el dockerfile que quermos que use
docker build -t platziapp -f build/development.Dockerfile .

docker build -t platziapp -f build/production.Dockerfile .
docker run --rm -it platziapp bas

```

## Docker in docker

* Manejar docker desde contenedores.
* Nos permite: si el proceso de build de integración continua corre dentro de un contenedor, puedo hablar al demond docker del servidor de integración continua.

```shell
# Montando a un contenedor el socket de docker
docker run -it --rm -v /var/run/docker.sock:/var/run/docker.sock docker:tagversion

# dive
docker run --rm -it -v /var/run/docker.sock:/var/run/docker.sock -v $(which docker):/bin/docker wagodman/dive:latest platziapp
```

