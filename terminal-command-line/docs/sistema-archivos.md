# Sistema de Archivos

* Se encarga de la organización de la información a traves de directorios (subdirectorios) y archivos. Formando el árbol de directorios.

## Archivo

* En el sistema operativo esta identificado por su nombre y su ubicación.
* Cada sistema operativo tiene normas para nombrar a los directorios y archivos, como por ejemplo el uso de caracteres especiales y la longitud del nombre.

### Archivos Virtuales

* Son punteros a directorios
* (..): Puntero al directorio padre.
* (.): Puntero al directorio actual.

## Comando

```bash
# Ver los archivos que hay en un directorio
path:~$ ls

# Ver todos los archivos y los ocultos
path:~$ ls -a

# Listar archivos y directorios
path:~$ ls -l
# Si inicia con d es un directorio

# Print Working Directory: Saber el path donde me encuentro
path:~$ pwd

# Cambiar de directorio
path:~$ cd directorio_a_donde_quiero_ir

# Ir al Home
path:~$ cs ~

# Ir al último directorio visitado
path:~$ cd -

## Comandos de organización de archivos
# Crear un directorio
path:~$ mkdir nombre_directorio

# Copiar un archivo
path:~$ cp origen destino

# Borrar el archivo
path:~$ rm nombre_archivo

# Mover un archivo
path:~$ mv origen destino

# Eliminar un directorio
path:~$ rmdir nombre_directorio
```

