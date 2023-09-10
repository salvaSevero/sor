# **Ejemplos Básicos en Docker**

!!! danger "Aviso"
    En los siguientes ejemplos el nombre del contenedor será Salva.

*  Crear un contenedor nuevo con la última versión de Ubuntu.

``` bash
docker run -d -it --name Salva ubuntu
```

*	Acceder al contenedor haciendo uso del intérprete /bin/bash.

``` bash
docker exec -it Salva bash
```

*	Actualiza los repositorios e instala dentro del contendor.

``` bash
apt-get update
apt-get install nano iputils-ping net-tools iproute2
```

*	Detén el contenedor desde la máquina anfitriona.

``` bash
docker stop Salva
```

*	Arranca el contenedor.

``` bash
docker start Salva
```

*	Descargar un fichero del contenedor a la máquina anfitriona.

``` bash
docker cp Salva:/home/prueba.txt .
```

*	Crear una imagen del contendor.

``` bash
docker commit Salva copiaContendor
```

*	Lista las imagenes que tienes en el sistema

``` bash
docker images
```

*	Crea un .tar de la imagen copiaContendor.

``` bash
docker image save -o /home/usuario/backup.tar copiaContendor
```

*	Saca la imagen del .tar y vuélcala en un contenedor. Recuerda estar en el mismo directorio que el .tar.

``` bash
docker load -i backup.tar
docker run -d -it --name NuevoContenedor copiaContendor
```