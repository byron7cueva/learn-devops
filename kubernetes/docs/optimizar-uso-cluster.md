# Optimizar el uso del Cluster

## Helm

* Es como un package manager para kubernetes.
* Nos ayuda a instalar o a desplegar algo de manera sencilla.
* https://github.com/helm/helm
* Se compone de dos componentes
  * Client site: Es la linea de comandos.
  * Componente dentro de kubernetes, que es server site que se llama tirer. 

```shell
# Configurar la herramienta
helm init

# Ver los pods del namespace admin
kubectl get pods -n kube-system
```

