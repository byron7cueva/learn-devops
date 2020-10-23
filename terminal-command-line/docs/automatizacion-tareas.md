# Automatizacion de tareas

## Scripting bash

* Se puede realizar scripts

```bash
#!/bin/bash
NEW_DIR=platzi

if [ ! -d "/root/$NEW_DIR" ]; then
	mkdir /root/$NEW_DIR
fi

cp backup_code.sh /root/$NEW_DIR/
echo "`date`: Todo listo jefe!"
```

* Ejecutarlos

```bash
user@path:~$ ./platzi.sh
```



## Programar tareas

```bash
# at 
# Indicando que se ejecute algo dentro de 2 minutos
usuario@pc:~$ at now +2 minutes

# cron utiliza una archivo que es el crontab que es la tabla de cron jobs
# Editar tareas y crear nuevas tareas
usuario@pc:~$ crontab -e

#minuto #hora #dia_mes #cual_mes #dia_semana #comando
45 12 * * * echo "Hola" > hola2.txt
```

