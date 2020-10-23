# Compresión de archivos

```bash
# El tamaño de de un archivo
usuario@pc:~$ ls archivo -lh
# Ver archivos que inicien en una palabra
usuario@pc:~$ ls palabra*

# Comprimir un archivo
usuario@pc:~$ gzip archivo

# Descomprimir
usuario@pc:~$ gzip -d archivo.gz
```

## Combinación de archivos

```bash
# Agrupar archivos en uno solo
# cf Create file
usuario@pc:~$ tar cf nombre.tar directorio/*

# Ver que contiene el archivo combinado
usuario@pc:~$ tar tf archivo.tar

# Extraer, o sacar del agrupamiento
usuario@pc:~$ tar xf archivo.tar

# Juntar y comprimir
usuario@pc:~$ tar czf nombre.tgz directorio/*

# Extraer
usuario@pc:~$ tar xzf nombre.tgz
```

