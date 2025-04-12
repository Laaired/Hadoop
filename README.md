# Hadoop
Practicas de hadoop
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





**Negritas**  
*cursiva*  

[url](https://github.com/Laaired/Hadoop/edit/main/README.md)  

`codigo`
