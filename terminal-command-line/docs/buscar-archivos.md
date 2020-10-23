# Buscar archivos

```bash
# locate permite hacer una busqueda en todo el sistema operativo indicandole solamente el nombre. Funciona a traves de una base de datos que tiene que ser actualizada explicitamente de forma periodica, por lo cual los archivos nuevos no los va encontrar
usuario@pc:~$ sudo updatedb
usuario@pc:~$ locate archivo

# whereis Se usa para ubicar archivos binarios osea comandos
# Es util cuando tenemos varias versiones de un ejecutable
usuario@pc:~$ whereis echo

# find Es la mas compleja, busca dentro de un arbol de directorios a partir de siertos criterios.
# usuario@pc:~$ find directorio -user nombre_usuario -perm 644 (permisios)
usuario@pc:~$ find . -user byron -perm 644
usuario@pc:~$ find . -user byron
# Solo archivos que han sido modificados en un intervalo de tiempo
# -mtime +7 mas de 7 dias
usuario@pc:~$ find . -type f -mtime +7
# Indicar lo que se quiere ejecutar sobre los archivos encontrados
# {} representa al nombre del archivo
# \; con eso se finaliza el comando
usuario@pc:~$ find . -type f -mtime +7 -exec cp {} ./backup/ \;
```