## Kubectl proxy

* Es un proxy que corre en foreground en user space.
* Nos permte acceder al API de Kubernetes de forma autentificada, desde dentro o fuera del cluster, y nos va authenticar automaticamente ya que utiliza las credenciales automáticas que usa kubectl.

```shell
# El servicio kubernetes es el servicio que esta eb cada uno de los nodos que expone el API Server 
kubectl get svc kubernetes

# Authenticarse y mandarlo a background
kubectl proxy &
# Nos indica que inicio un servidor en la ip local a la cual nos podemos conectar, haciendo un bind a un puerto del equipo local
curl http://localhost:8001
curl http://localhost:8001/version

# Mandar un proceso a foreground
fg


# Ayuda
kubectl proxy --help
```



## Kubectl Port fordware

* Nos permite hacer lo mismo que el kubectl proxy, pero para poder acceder a cualquier puerto de cualquier servicio que este expuesto en el cluster.

```shell
# Hacer un tunel para poderce conectar
# kubectl port-fordward servicio puerto_local:puerto_cluster
kubectl port-fordward svc/redis 10000:6379
telnet localhost 10000
```

