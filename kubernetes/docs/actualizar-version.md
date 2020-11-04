# Actualizar versión de la aplicacion

## Rolling Operates

* Es el mecanismo que utiliza kubernates para actualizar la version de una aplicación.

```shell
# Obtener el output de todos los deployments
kubectl get deploy -o json

kubectl get deploy -o json | jq ".items[] | {name:.metadata.name} + .spec.strategy.rollingUpdate"
```

* maxSurge:  Cuantos Pods se crean a partir de los que tengo. Por ejemplo con maxSurge:25%, eso quiere decir que de 100 hasta 25 Pods pueden estar creandose al mismo tiempo, eso quiere decir que como minimo tendria 50 Pods que estan disponibles al momento de hacer un run upperates o creandose al mismo tiempo.
* maxUnavailable: En un detenerminado momento del deploy puede ver hasta un % de Pods que no esten disponibles, pueden estar en un estado que esten iniciando o empezando.

```shell
# Ver los replicasets
kubectl get replicasets -w

# Run Upperate de la aplicacion
kubectl set image deploy worker worker=dockercoins/worker:v0.2

# Regresar a una version anterior
# Desaser el ultimo rollout del deploy
kubectl rollout undo deploy worker

# Cambiar parametros de deployment de a estrategia de deploy
kubectl edit deploy worker
# Para ver si volvi a la ultima version
kubectl rollout status deployment worker

kubectl get deploy -o json worker | jq ".items[] | {name:.metadata.name} + .spec.strategy.rollingUpdate"

# Dejar al cluster a un estado anterior
kubectl rollout undo deploy worker
```

