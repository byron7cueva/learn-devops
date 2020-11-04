# Balanceo de carga

## Escalar en un Pod o container

### DaemondSet

* Kubernetes no permite crear DaemondSet a traves de kubectl. Para ello se debe crear a traves de los manifest files.
* Es la forma de squeliar un Pod o asignar un Pod a cada nodo corra unica instancia solamente.

```shell
# Exportar una definicion de un deployment
kubectl get deploy/rng -o yaml --export > rng.yml

kubectl apply -f rng.yml --validate=false

# Obtener Pods a traves de un label
kubectl get pods --selector=app=rng

# Quitar un label llamado app
kubectl label pod nombre_pod app-
```

