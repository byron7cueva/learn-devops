# Dashboard

* Se crea en otro namespace (kube-system) ya que necesita acceder a componentes del sistema de kubernetes.
* Por defecto cuando se accede al dashboard no estamos autentificados. Se puede authentificar a traves de dos maneras:
  * Kubeconfig: Es el archivo config que se encuentra en la maquina local.
  * Token: Un token de configuración que se puede gestionar en el cluster.

```shell
# Desplegar el dashboard
# apply permite desplegar recursos de kubernetes de manera atomica
# -f aplicar un archivo
kubectl apply -f kubernetes-dashboard.yaml

kubectl get service -n kube-system

# Editar la definicion del servicio
kubectl edit service kubernetes-dashboard -n kube-system

# Aplicar un archivo de configuracion para permisos de administrador
# Crea un RolBinding
kubectl apply -f grant-admin-to-dahsboard.yaml
```

