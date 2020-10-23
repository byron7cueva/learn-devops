# Archivos

## Tipos

* **Binarios:** Son auqellos que estan pensados y escritos de una manera para que sea interpretado con una computadora, como por ejemplo: Programas ejecutables, archivos de datos, documentos, fotos, videos, etc
* **De texto:** También su contenido es binario, sin embargo los binarios que contiene son aquellos que corresponden con caracteres, si se lo abre con un editor de texto se lo puede leer sin ningun inconveniente. Estos son por ejemplo: Configuraciones. paginas web o el codigo fuente de un programa.

## Archivos de Texto

### Utilidades interactivas

* Programas que procesan texto en tiempo real.

* Esto quiere decir que el programa va reaccionar al commando que vayamos a ejecutar inmediatamente.

  * vim

    Comandos

    i Insertar texto

    ESC Salir del modo de edición

    : Activo el modo de comandos

    w Guardo el contenido

    :x Grabar y salir a la vez

    :q Salir de vim

  * nano

    Directamente estoy en modo de edición

    CTRL X: Salir del programa

### Utilidades batch (procesamiento por lotes)

* Son programas que procesan texto y emiten el resultado.

* A estas herramientas se les pasa toda información que se necesita al momeanto de la invocación para que luego nos devuelva los resultados.

* Es bueno utilizar estas utilidades en batch cuando se quiere hacer una modificación puntual en un rachivo muy grande, espcialmente cuando esa modificación debe hacerse sobre muchos archivos similares.

  

  ```bash
  # Mostrar el contenido completo de un archivo
  user@path:~$ cat nombre_archivo
  
  # Muestra las primeras lineas del archivo
  user@path:~$ head nombre_archivo
  
  # Ver las primeras 5 lineas
  user@path:~$ head -n 5 nombre_archivo
  
  # Ver las ultimas 5 lineas de un archivo
  user@path:~$ tail -n 5 nombre_archivo
  ```

### Utilidades batch avanzadas

```bash
# Grep
# Búsqueda por expresiones regulares
# Busca las lineas en archivos de texto a través de expresiones regulares
user@path:~$ grep palabra archivo

# Buscar sin tomar en cuenta si esta con mayúsculas y minúsculas
user@path:~$ grep -i palabra archivo

# Buscar una frace que termine con una palabra
user@path:~$ grep -i "palabra$" archivo

# Sed 
# String editor
# Tratamiento de flujos de caracteres
# Trabaja sobre un flujo de texto, como un archivo de texto
# Utiliza expresiones regulares, permite reemplazar una expresión por otra, pero no modifica el archivo
# Sustitucion
# /g modificador que indica que se debe hacer por todo el flujo
user@path:~$ sed 's/palabraBuscada/palabraRemplaza/g' archivo

# Eliminarla ultima linea
user@path:~$ sed '$d' nombre_archivo

# Awk
# Tratamiento de texto delimitado
# Sirve muy bien para trabajar con textos estructurados, como por ejemplo como archivos separados por comas o tabs o alguna cosa similar.
# Tiene un lenguaje de escripting
# user@path:~$ awk -F 'delimitador' '{ print $numeroColuma }' nombre_archivo
# Extrae solo la primera columna
user@path:~$ awk -F ';' '{ print $1 }' nombre_archivo

# Número de linea sea mayor de 1 (Quitando los encabezados) y la tercera columna es mayor que cero.
# Tambien se puede hacer calculos entre columnas
user@path:~$ awk -F ';' 'NR > 1 && $3 > 0 { print $1, $3 * $4 }' nombre_archivo
```



