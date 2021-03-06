# Taller de Modularización con Virtualización e Introducción a Docker y a AWS
## Descripción
El taller consiste en crear una aplicación web pequeña usando el micro-framework de Spark java (http://sparkjava.com/). Una vez tengamos esta aplicación procederemos a construir un container para docker para la aplicación y los desplegaremos y configuraremos en nuestra máquina local. Luego, cerremos un repositorio en DockerHub y subiremos la imagen al repositorio. Finalmente, crearemos una máquina virtual de en AWS, instalaremos Docker , y desplegaremos el contenedor que acabamos de crear.


## Prerrequisitos
Para la realización y ejecución tanto del programa como de las pruebas de este, se requieren ser instalados los siguientes programas:
* [Maven](https://maven.apache.org/). Herramienta que se encarga de estandarizar la estructura física de los proyectos de software, maneja dependencias (librerías) automáticamente desde repositorios y administra el flujo de vida de construcción de un software.
* [GIT](https://git-scm.com/). Sistema de control de versiones que almacena cambios sobre un archivo o un conjunto de archivos, permite recuperar versiones previas de esos archivos y permite otras cosas como el manejo de ramas (branches).
* [Docker](https://www.docker.com/). Programa encargado de crear contenedores ligeros y portables para las aplicaciones software que puedan ejecutarse en cualquier máquina con Docker instalado, independientemente del sistema operativo que la máquina tenga por debajo, facilitando así también los despliegues.

Para asegurar que el usuario cumple con todos los prerrequisitos para poder ejecutar el programa, es necesario disponer de un Shell o Símbolo del Sistema para ejecutar los siguientes comandos para comprobar que todos los programas están instalados correctamente, para así compilar y ejecutar tanto las pruebas como el programa correctamente.

```
mvn -version
git --version
java -version
docker version
```

## Instalación
Para descargar el proyecto de GitHub, primero debemos clonar este repositorio, ejecutando la siguiente línea de comando en GIT.

```
git clone https://github.com/Oredreim/Modularizacion.git
```

## Ejecución
Para compilar el proyecto utilizando la herramienta Maven, nos dirigimos al directorio donde se encuentra alojado el proyecto, y dentro de este ejecutamos en un Shell o Símbolo del Sistema el siguiente comando:

```
mvn package
```

## Pruebas
Para realizar las pruebas correspondientes del proyecto utilizando la herramienta Maven, nos dirigimos al directorio donde se encuentra alojado el proyecto, y dentro de este ejecutamos en un Shell o Símbolo del Sistema el siguiente comando:

```
mvn test
```

Pruebas compiladas correctamente para el código fuente **RoundRobin**.

![alt text](https://github.com/Oredreim/Modularizacion/blob/main/img/testRoundRobin.png?raw=true)



### Localhost

Para probar ahora el correcto funcionamiento del Docker de manera local o localhost del programa **RoundRobin**, primero ejecutamos los siguientes comandos en orden.

```
docker-compose up -d
docker images
docker ps
```

![alt text](https://github.com/Oredreim/Modularizacion/blob/main/img/3.png?raw=true)

Ahora para acceder al proyecto ejecutamos el siguiente comando:
```
http://<IP asignada>:35000
```

![alt text](https://github.com/Oredreim/Modularizacion/blob/main/img/4.png?raw=true)

### Despliegue DockerHub

Ingresamos a la cuenta y creamos un nuevo repositorio

![alt text](https://github.com/Oredreim/Modularizacion/blob/main/img/5.png?raw=true)

Creamos las imagenes para el Dockerhub

![alt text](https://github.com/Oredreim/Modularizacion/blob/main/img/6.png?raw=true)

Realizamos el push en el repositorio de docker

![alt text](https://github.com/Oredreim/Modularizacion/blob/main/img/7.png?raw=true)

Pero por alguna razon nunca me logre conectar con docker desde consola

![alt text](https://github.com/Oredreim/Modularizacion/blob/main/img/8.png?raw=true)

### AWS
Creacion maquina virtual.

![alt text](https://github.com/Oredreim/Modularizacion/blob/main/img/9.png?raw=true)

Desplegamos una LINUX 2AMI (HVM)

![alt text](https://github.com/Oredreim/Modularizacion/blob/main/img/10.png?raw=true)

Continuamos y seleccionamos la opcion gratuita

![alt text](https://github.com/Oredreim/Modularizacion/blob/main/img/11.png?raw=true)

Y procedemos a crear y descargar las llaves RSA

![alt text](https://github.com/Oredreim/Modularizacion/blob/main/img/12.png?raw=true)

Movemos nuestra llave a una carpeta para poder manipularla mejor

![alt text](https://github.com/Oredreim/Modularizacion/blob/main/img/13.png?raw=true)

Le damos permiso de ejecucion y mandamos la conexion por SSH

![alt text](https://github.com/Oredreim/Modularizacion/blob/main/img/14.png?raw=true)

Actualizamos la maquina.

![alt text](https://github.com/Oredreim/Modularizacion/blob/main/img/15.png?raw=true)

Instalamos Docker y volvemos a ingresar para ahora si desplegarlo

![alt text](https://github.com/Oredreim/Modularizacion/blob/main/img/16.png?raw=true)

Ahora pasamos a confirgurar los puertos, para esto abriremos nuevamente en el browser la consola, nos dirijiremos a `instancias`  y luego a `segurida` entonces encontraremos la seccion de `inbound rules`.

![alt text](https://github.com/Oredreim/Modularizacion/blob/main/img/16.png?raw=true)

![alt text](https://github.com/Oredreim/Modularizacion/blob/main/img/17.png?raw=true)

Agregaremos las reglas y asignaremos puertos por regla.

![alt text](https://github.com/Oredreim/Modularizacion/blob/main/img/18.png?raw=true)

![alt text](https://github.com/Oredreim/Modularizacion/blob/main/img/19.png?raw=true)

Guardamos y realizamos los despliegues de la misma manera que hicimos de manera local, pero ahora en la maquina de AWS.

## Construido con
* [Maven](https://maven.apache.org/). Herramienta que se encarga de estandarizar la estructura física de los proyectos de software, maneja dependencias (librerías) automáticamente desde repositorios y administra el flujo de vida de construcción de un software.
* [GIT](https://git-scm.com/). Sistema de control de versiones que almacena cambios sobre un archivo o un conjunto de archivos, permite recuperar versiones previas de esos archivos y permite otras cosas como el manejo de ramas (branches).
* [JUnit](https://junit.org/junit5/). Framework de Java que permite la realización de la ejecución de clases de manera controlada, para poder comprobar que los métodos realizan su cometido de forma correcta.
* [Eclipse](https://www.eclipse.org/ide/). Entorno de desarrollo integrado (IDE) utilizado en programación de computadoras. Contiene un espacio de trabajo básico y un sistema de complementos extensible para personalizar el entorno. Eclipse está escrito principalmente en Java y su uso principal es para desarrollar aplicaciones Java, pero también se puede usar para desarrollar aplicaciones en otros lenguajes de programación a través de complementos (plug-ins).
* [Java](https://www.oracle.com/java/). Lenguaje de programación de propósito general, es decir, que sirve para muchas cosas, para web, servidores, aplicaciones móviles, entre otros. Java también es un lenguaje orientado a objetos, y con un fuerte tipado de variables.
* [Docker](https://www.docker.com/). Programa encargado de crear contenedores ligeros y portables para las aplicaciones software que puedan ejecutarse en cualquier máquina con Docker instalado, independientemente del sistema operativo que la máquina tenga por debajo, facilitando así también los despliegues.
* [AWS](https://aws.amazon.com/es/). Conjunto de herramientas y servicios de cloud computing de Amazon, que engloba una gran cantidad de servicios para poder realizar distintos tipos de actividades en la nube. Desde almacenamiento a la gestión de instancias, imágenes virtuales, desarrollo de aplicaciones móviles, etc.
* [CircleCI](https://circleci.com/). Plataforma moderna de integración continua y entrega continua (CI / CD) que se encarga de automatizar la construcción, pruebas e implementación de software.
* [Obsidian](https://obsidian.md). Obsidian is a powerful knowledge base on top of
a local folder of plain text Markdown files.

## Autor
[Cristian Piñeros](https://github.com/Oredreim)
## Licencia & Derechos de Autor
**©** Cristian Camilo Piñeros Arevalo, Estudiante de Ingeniería de Sistemas de la [Escuela Colombiana de Ingeniería Julio Garavito](https://www.escuelaing.edu.co/es/).

Licencia bajo la [GNU General Public License](https://github.com/Oredreim/Modularizacion/blob/main/LICENSE).
