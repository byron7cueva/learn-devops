# Healthchecks

* Es el mecanismo que tiene kubernetes de saber si la aplicación esta funcionando de manera correcta, para saber si tiene que reiniciarla o removerla de algún servicio de manera que no le envié trafico por la cuestión que la aplicación no esta en un estado deseado.
* Tiene dos tipos:
  * Liveness
    * Indican errores de los cuales la aplicación no se puede recuperar.
    * A través de un flag failure-freshool, suele ser un numero entre 3 a 5. Va intentar ejecutar ese healthcheck hasta que se supere ese failure-freshool y cuando se supere, elimina el Pod y vuelve a crear uno nuevo con la misma versión intentando ver si se recupera. Esto va hacerlo hasta dejar de intentar crear Pod porque ya sabe que no lo puede hacer.
  * Reiness Pro
    * Puede ser un error temporal.
    * Kubernetes lo que hace es remueve temporalmente esa aplicación del servicio hasta que el Reiness no se encuentre en true, kubernetes no va poder enviar trafico.
  * Cada uno de los healhchecks se los puede especificar de las siguiente maneras:
    * HTTP: Si el Pod expone una API o servicio web. Yo puedo crear un healthcheck de tipo HTTP, para decir accedo a mi aplicación a /status y si me devuelve un status 200, eso quiere decir tanto el Liness y Reiness estan OK para que kubernetes orqueste ese servicio.
    * TCP Pro: Va intentar acceder al puerto del servicio y si se puede conectar, y la conexión TCP se establece entonces kubernetes va marcarlo como OK.
    * Custom exec: Esto quiere decir que puedo ejecutar un comando dentro del contenedor. Y el resultado de ese comando va ser tomado como el resultado del Healthcheck, si el resultado es 0 va ser OK y si es diferente de 0, entonces los healthcheck van a dar incorrecto.

```shell
kubectl edit deploy/redis
```

```yaml
# Va en la parte de containers
containers:
- image: redis
  name: redis
  livenessProbe:
    exec:
      command: ["redis-cli", "ping"]
```

```shell
# Ver el estado del healthcheck
kubectl describe pod nombre_pod

# Ver el status code
echo $?
```



