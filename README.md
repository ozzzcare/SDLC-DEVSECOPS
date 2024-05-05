# SDLC-DEVSECOPS
Practica 2 S-SDLC - DevSecOps 
# SDLC

##  APP TO-DO DOCKER

## DEFINICIÓN

La actividad se ha llevado a cabo estudiando la aplicacion TO-DO, que forma parte del tutorial de inicio de Docker. 
Para ejecutarla, se ha tratado de aplicar S-SDLC con el objetivo de seguir una metodologia de desarrollo seguro desde el inicio del proyecto. La guia tutorial de Docker muestra el paso a paso, incluida la instalacion de las herramientas necesarias, para crear una imagen, contenizarla y enviarla a un repositorio, habiendo logrado un resultado satisfactorio. Para ello, se ha seguido el siguiente protocolo: 

 - Identificacion y seleccion de la aplicacion.
 - Creacion de la estructura del proyecto.
 - Desarrollo de las consideraciones de S-SDLC.
 - Implementacion
 - Pruebas
 - Conclusiones

## IDENTIFICACION DE LA APLICACION

La aplicacion seleccionada es un TO-DO LIST, que bien podemos utilizar de forma local o podemos disponer de ella a traves de nuestro repositorio en Docker. 

## ESTRUCTURA DEL PROYECTO

Para llevar a cabo la ejecucion de la aplicacion necesitamos las siguientes herramientas:

* Dockerfile - Archivo de texto que contendra el codigo fuente.
* Docker Hub - https://www.docker.com/products/docker-hub/ - Empleado para desplegar la aplicacion dentro del contenedor de software.
* Visual Studio Code - https://code.visualstudio.com/ - Empleado para editar el codigo fuente en un entorno seguro
* Git Bash - https://git-scm.com/book/es/v2/Ap%C3%A9ndice-A%3A-Git-en-otros-entornos-Git-con-Bash Utilizado para acceder a caracteristicas del terminal de forma mas manejable e identificar problemas de seguridad en el codigo. 
* SAST - https://owasp.org/www-community/Source_Code_Analysis_Tools Herramienta para analizar las lineas de codigo obtenido de fuentes externas para evitar inyecciones de SQL u otras vulnerabilidades.
* Docker Playground - https://www.docker.com/play-with-docker/ - Herramienta para el test de nuestra aplicacion.

## PARTICIPANTES 
* PABLO SERNA ARRAZOLA - https://github.com/paserarra0/to-do
* OSCAR MELIM HERNANDEZ - https://github.com/ozzzcare/proyecto-sdlc
* MIGUEL ANGEL VELAZQUEZ RODELA - PENDING TO ADD

## ANÁLISIS DE PROYECTOS ANTERIORES

Con respecto al proyecto anterior entregado, los tres partcipantes hemos desarrollado la WEB-APP del TO-DO List de Docker, siguiendo todas las consideraciones que el propio tutorial de Docker indica. Sin embargo, tras analizar los resultados de estas aplicaciones, se observa que deben incluirse mayores medidas de seguridad con respecto a su ejecución e implementación. 


## CICLO DE VIDA DE DESARROLLO DE SOFTWARE (SDLC)

Para aplicar un enfoque metodologico para el desarrollo de software, necesita aplicarse desde la concepcion de la idea hasta el despliegue del producto. Para ello, nos aseguramos que todas las herramientas utilizadas provengan de fuentes fiables, donde no se hayan podido producir brechas de seguridad que vulnere nuestro dispositivo. Para añadir una capa extra de seguridad, podemos llevar a cabo la fase de pre-produccion en una maquina virtual (desde VirtualBox), con una consola Ubuntu, desde la cual podemos obtener un mayor control de los puertos que utilizamos para el uso de Docker. 

Todas las lineas de codigo empleadas para nuestra aplicacion deben pasar por una herramienta de analisis estatico que nos alerte de fallos en el codigo y sobretodo de vulnerabilidades.

## CONSIDERACIONES DE SEGURIDAD 


## DevSecOps

A continuación se indica la metodología seleccionada para aplicar el enfoque DevSecOps, donde se establecen los principios para un desarrollo seguro desde la creación del software. 

1. Planificación y Diseño:
 
Identificación de Requisitos de Seguridad: Antes de comenzar el desarrollo, se deben identificar los requisitos de seguridad específicos para la aplicación "To Do List". Esto incluye la autenticación de usuarios, los permisos que cada usuario posee y la protección de datos sensibles como: 

* Datos de Identificación Personal
* Información sensible que se añada al To-Do
* Contraseñas y Credenciales de acceso

2. Desarrollo:
 
Utilización de Imágenes Seguras: Al construir la aplicación en contenedores Docker, es esencial utilizar imágenes base seguras y actualizadas. Para ello se van a utilizar herramientas como Docker Content Trust para garantizar que solo se utilicen imágenes de confianza.

Codificación Segura: Se van a implementar buenas prácticas de codificación segura para prevenir vulnerabilidades comunes, como la inyección de código malicioso o la exposición de datos sensibles. Asimismo, se emplearán herramientas de análisis estático de código (SAST) para identificar posibles problemas de seguridad durante el desarrollo.

3. Pruebas:
 
Se considera integrar pruebas de seguridad automatizadas en el proceso de integración continua (CI) para detectar vulnerabilidades tempranas en el ciclo de desarrollo. Esto puede incluir pruebas de penetración o escaneo de vulnerabilidades de contenedores. 

4. Implementación:
 
Para su implementación se llevará a cabo el despliegue de la aplicación en un entorno seguro. Este entorno seguro será el mismo considerado para el Ciclo de Vida de Desarrollo de Software (SDLC), es decir, se llevará a cabo la pre-producción de la aplicación desde una máquina virtual que nos permita proteger y limitar la exposición de los sistemas, así como mantener el control de los puertos abiertos.  

A su vez, se aplicarán políticas de control de acceso adecuadas para limitar quién puede modificar la infraestructura y el código de la aplicación.

5. Monitoreo y Mantenimiento:
 
Se implementará el monitoreo continuo de seguridad para detectar y responder a posibles ataques o vulnerabilidades en tiempo real. Esto podrá incluir la supervisión de registros, la detección de anomalías y el análisis del comportamiento del usuario.

A su vez se mantendrán actualizados todos los componentes de la aplicación, incluidos los contenedores Docker y las dependencias de software, para mitigar posibles riesgos de seguridad.

## DIAGRAMA S-SDLC & DevSecOps


## IMPLEMENTACION

Instalar Docker 
Instalar Git Bash
Instalar Visual Studio Code

1. CLonar el repositorio del to-do app: 
```bash
git clone https://github.com/docker/getting-started-app.git
```
2. Crear Dockerfile que guarde el contenido del repositorio: 
```bash
# syntax=docker/dockerfile:1

FROM node:18-alpine
WORKDIR /app
COPY . .
RUN yarn install --production
CMD ["node", "src/index.js"]
EXPOSE 3000
```
3. Nos aseguramos de estar en el directorio correcto, para asi evitar construir la imagen en un lugar que no corresponde. Utilizamos el siguiente comando para ello: 
```bash
cd /(your_route)/to/getting-started-app
```
4. Construimos la imagen. 
```bash
docker build -t getting-started .
```
5. Iniciamos un contenedor de aplicaciones. Este ira en el puerto que escojamos. Siguiendo el ejemplo, se utilizara el puerto 3000. 
```bash
docker run -dp 127.0.0.1:3000:3000 getting-started
```
6. Acudiendo a la siguiente ruta, ya deberiamos obersar nuestro to-do. 
 http://localhost:3000 .

 7. Creamos un repositorio en docker. que le daremos un nombre. Con este nombre etiqueremos nuestra imagen previa:
 ```bash
docker tag getting-started YOUR-USER-NAME/getting-started
```
8. Una vez renombrada, ya podemos ejecutar nuestra imagen para pasar de local a hub. Previamente, tendremos que identificar nuestro repositorio Docker, y haberlo asignado a nuestro usuario con nuestra contraseña. En este punto hay que tener cuidado ya que no es recomendable desde el punto de vista de seguridad añadir nuestras contraseñas en las lineas de codigo. Para ejecutar la imagen seguimos: 
```bash
docker push YOUR-USER-NAME/getting-started
```
9. A traves de Docker Play podemos iniciar nuestra aplicacion, donde deberiamos ver nuestra imagen desplegada: 
 ```bash
docker run -dp 0.0.0.0:3000:3000 YOUR-USER-NAME/getting-started
```

## CONCLUSIONES

Se reconoce la importancia del Ciclo de Vida de Desarrollo de Software (SDLC) para garantizar un desarrollo seguro desde el inicio del proyecto hasta su despliegue y mantenimiento. 
Se ha identificado y seleccionado una aplicacion existente (TO-DO) como referencia y se ha creado una estructura de proyecto que incluye los archivos y herramientas necesarios. 
Se han desarrollado consideraciones de seguridad utilizando el SDLC, aplicando tareas de seguridad en cada etapa. 
Se ha seguido un proceso paso a paso para implementar la aplicacion utilizando Docker, destacando la importancia de garantizar la seguridad en cada paso. 
Se han utilizado diversas herramientas de seguridad, como Git Bash, Visual Studio Code y Docker Playground, para garantizar la seguridad durante el desarrollo y despliegue de la aplicacion.
