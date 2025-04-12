# Hadoop
Practicas de hadoop

# Instalación 

## Clonar el repositorio Docker-Hadoop de Github  
* Ir al repositorio [Docker](https://github.com/big-data-europe/docker-hadoop)  
* Dar click en Code y después Download ZIP

UnZip el archivo descargardo y guardelo en un carpeta.  

## Inicie el contenedor de Docker  
* Abre una terminal dentro de la carpeta donde guardaste el proyecto de Docker-Hadoop.

* Escribe este comando: docker-compose up -d
Esto iniciará automáticamente los 5 contenedores necesarios para Hadoop. La primera vez puede tardar un poco porque se descargan archivos desde internet.

### ¿Cómo saber si ya están funcionando los contenedores?  

* Puedes escribir `docker ps` en la terminal.  

* O abrir Docker Desktop y verificar que los contenedores están corriendo.

## Para entrar al contenedor principal (namenode):  

* Escribe: `docker exec -it namenode bash`

Esto te lleva dentro del contenedor del nodo maestro de Hadoop, como si estuvieras usando una pequeña computadora con Linux. Desde ahí puedes administrar el sistema de archivos HDFS

## Visualice el panel de control en su host local
Acceda a *localhost:9870* en su navegador

## Apagar los contendores

* Abrimos Docker Desktop  
* Damos click en el botón stop  de  contenedor docker-hadoop.

# Estructura general del sistema Hadoop  

## Entrar al nodo maestro (namenode):

* Escribe en la terminal:
`docker exec -it namenode bash`

Esto te da acceso al contenedor principal de Hadoop, como si entraras a una mini computadora con Linux.

## Crear carpetas en el sistema de archivos de Hadoop (HDFS):

* Primero, puedes ver qué carpetas existen escribiendo:
`hdfs dfs -ls /`

* Hadoop necesita una carpeta con esta ruta: `/user/root/`, así que la creamos con:  
`hdfs dfs -mkdir -p /user/root/`

* Para confirmar que se creó correctamente, puedes verificarlo con:
`hdfs dfs -ls /user/`

# *Ejemplo que puedes realizar*

## Resolver un Sudoku con Hadoop y MapReduce  

### Descargar archivos necesarios:

* Baja el archivo hadoop-examples-0.20.205.0.jar, que contiene el código para resolver el Sudoku.

* También descarga el archivo puzzle1.dta, que contiene el Sudoku a resolver.

* Mueve ambos archivos a la carpeta donde tienes tu proyecto docker-hadoop.

### Copiar los archivos al contenedor de Hadoop:

* Abre una terminal y ejecuta:

`docker cp hadoop-examples-0.20.205.0.jar namenode:/tmp`  
`docker cp puzzle1.dta namenode:/tmp`

Entrar al contenedor namenode: `bash`

`docker exec -it namenode bash`

### Ejecutar el algoritmo MapReduce:

* Cambia a la carpeta /tmp dentro del contenedor:
  `cd /tmp`

### Ejecuta el programa que resuelve el Sudoku:

`hadoop jar hadoop-examples-0.20.205.0.jar sudoku puzzle1.dta`

### Guardar el resultado en un archivo de texto:

* Para guardar la solución en un archivo llamado `solucion_puzzle1.txt`, ejecuta:

`hadoop jar hadoop-examples-0.20.205.0.jar sudoku puzzle1.dta > solucion_puzzle1.txt`

### Luego sal del contenedor con:

`exit`

### Copiar el archivo de solución a tu computadora:

* Ejecuta:

`docker cp namenode:/tmp/solucion_puzzle1.txt .`

*(Recuerda que el punto al final significa “copia a la carpeta actual”)*

### Ver el resultado:

* Abre el archivo solucion_puzzle1.txt que ahora está en tu carpeta del proyecto docker-hadoop.

## ¿Qué se aprendió con esta práctica de Hadoop?  

### Cómo usar Hadoop sin complicaciones:  

* Usamos un programa llamado Docker para crear un entorno donde Hadoop puede funcionar sin tener que instalar todo manualmente.

### Cómo guardar y ver archivos dentro de Hadoop:  

* Aprendimos que Hadoop tiene su propio sistema de carpetas (como una computadora), y supimos cómo crear y ver esas carpetas con comandos especiales.

### Cómo resolver un problema (un Sudoku) usando Hadoop:  

* Usamos un archivo especial que ya trae el código para resolver sudokus. Le dimos un sudoku como entrada, y Hadoop lo resolvió por nosotros.

### Cómo mover archivos entre nuestra compu y Hadoop:

* Aprendimos cómo pasar archivos a Hadoop y cómo traerlos de vuelta para ver los resultados.

### Cómo manejar los contenedores (máquinas virtuales pequeñas):

* Supimos cómo prender, entrar y apagar estos contenedores donde corre Hadoop.

# *¡FELICIDADES! ¡Somos los mejores aprendiendo!*
