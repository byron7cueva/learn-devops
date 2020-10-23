# Variables de Entorno

* Es una definicion global a la que todos los procesos tienen acceso, para obtener más información.
* PATH: En esta varibale se almacena todas las rutas donde el interprete debe ir a buscar los archivos que pueden ser ejecutables. Esta definida en /etc/enviroment

```bash
# Asignar a toda la sesion
usuario@pc:~$ export VAR=valor

# Asignacion para una ejecucion particular
usuario@pc:~$ VAR=valor comando

# Agregar un valor en
# .bashrc
export PATH=$PATH:/home/byron/bin

# Actualizar
usuario@pc:~$ source .bashrc
```

