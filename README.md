# SDLC-DAST - SAST - RASP
Practica 3 DAST - SAST - RASP 
# SDLC

##  APP TO-DO DOCKER

## DEFINICIÓN

La actividad se ha llevado a cabo estudiando las aplicaciones TO-DO que los integrantes del grupo desarrollamos en l primera actividad.
Esta aplicación cuenta con la implementación del S-SDLC así como del DevSecOps, metodologías que proporcionan un enfoque seguro para el proceso end-to-end del desarrollo. 
La guia tutorial de Docker muestra el paso a paso para la ejecución de la aplicacición, incluida la instalacion de las herramientas necesarias para crear una imagen, contenizarla y enviarla a un repositorio, habiendo logrado un resultado satisfactorio. Para ello, se ha seguido el siguiente protocolo: 

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
* Docker Playground - https://www.docker.com/play-with-docker/ - Herramienta para el test de nuestra aplicacion.
* SAST - Docker Bench Security
* SAST - https://owasp.org/www-community/Source_Code_Analysis_Tools Herramienta para analizar las lineas de codigo obtenido de fuentes externas para evitar inyecciones de SQL u otras vulnerabilidades.
* DAST - https://www.zaproxy.org/
* RASP - Trivy - Escáner de seguridad de código abierto más popular, fiable, rápido y fácil de usar. Utilice Trivy para encontrar vulnerabilidades y configuraciones erróneas de IaC - Guía de instalación: https://aquasecurity.github.io/trivy/v0.17.2/
  

## PARTICIPANTES 
* PABLO SERNA ARRAZOLA - https://github.com/paserarra0/to-do
* OSCAR MELIM HERNANDEZ - https://github.com/ozzzcare/proyecto-sdlc
* MIGUEL ANGEL VELAZQUEZ RODELA - https://github.com/Tekurojo/Proyecto-SDLC-to-do
  

## ANÁLISIS DE PROYECTOS ANTERIORES

Con respecto al proyecto anterior entregado, los tres partcipantes hemos desarrollado la WEB-APP del TO-DO List de Docker, siguiendo todas las consideraciones que el propio tutorial de Docker indica. Sin embargo, tras analizar los resultados de estas aplicaciones, se observa que deben incluirse mayores medidas de seguridad con respecto a su ejecución e implementación. 


## CICLO DE VIDA DE DESARROLLO DE SOFTWARE (SDLC)

Para aplicar un enfoque metodologico para el desarrollo de software, necesita aplicarse desde la concepcion de la idea hasta el despliegue del producto. Para ello, nos aseguramos que todas las herramientas utilizadas provengan de fuentes fiables, donde no se hayan podido producir brechas de seguridad que vulnere nuestro dispositivo. Para añadir una capa extra de seguridad, podemos llevar a cabo la fase de pre-produccion en una maquina virtual (desde VirtualBox), con una consola Ubuntu, desde la cual podemos obtener un mayor control de los puertos que utilizamos para el uso de Docker. 

Todas las lineas de codigo empleadas para nuestra aplicacion deben pasar por una herramienta de analisis estatico que nos alerte de fallos en el codigo y sobretodo de vulnerabilidades.

Tanto el Ciclo de Vida de Desarrollo de Software (SDLC) como la metodología DevSecOps han sido esenciales para garantizar el desarrollo seguro de nuestro proyecto.
Para concluir, las medidas adoptadas tanto del punto de vista DevSecOps y S-SDLC son las siguientes:
* Creación de usuarios y permisos
* Utilización de imágenes seguras (Docker Content Trust)
* Análisis estático de código
* Pruebas de seguridad automatizadas
* Implementación en una máquina virtual segura (control de puertos)
* Actividades de monitoreo y mantenimiento de la aplicación

## CONSIDERACIONES DE SEGURIDAD 

Se incluye como consideraciones de seguridad para el proyecto:

Ejecutar tu aplicación Docker sin ser usuario root y con los mínimos privilegios. Beneficios de ejecutar tu aplicación sin ser usuario root:

-Seguridad: Ejecutar tu aplicación sin ser usuario root ayuda a reducir la superficie de ataque y a proteger tu sistema de ataques.
-Aislamiento: Ejecutar tu aplicación en un contenedor aislado ayuda a proteger tu sistema de otros procesos que se ejecutan en el host.
-Portabilidad: Las aplicaciones que se ejecutan en contenedores son más portátiles y se pueden ejecutar en cualquier sistema que tenga Docker instalado. 

Para ejecutar tu aplicación Docker sin ser usuario root y con los mínimos privilegios, se siguen estos pasos:

1. Definir un usuario no root: Crea un usuario no root en tu sistema Docker host que tendrá los permisos necesarios para ejecutar tu aplicación. Para ello utilizaremos el siguiente comando:   
```bash
sudo useradd -r -m
```

Este comando creará un usuario root con un directorio personal y establecerá los permisos adecuados para que el usuario pueda ejecutar los comandos.

2. Crear un grupo para la aplicación: Para ello utilizaremos el siguiente comando:
```bash
sudo groupadd
```

3. Agregar el usuario creado en el paso 1 al grupo que creado en el paso 2 utilizando el siguiente comando:
```bash
 sudo usermod -aG
```

4. Establece los permisos de archivo correctos: Utilizando el comando chmod podemos establecer los permisso de archivo para no otorgar permisos de escritura a ninguún archivo que no lo necesite. 

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
![DIAGRAM SSDLC](https://github.com/ozzzcare/SDLC-DEVSECOPS/assets/166165564/df7840b0-61e8-486b-90a8-9b21e0df892d)
![DIAGRAM DEVSECOPS](https://github.com/ozzzcare/SDLC-DEVSECOPS/assets/166165564/ad29a6c6-9d9a-48bf-8800-0a88491eea4c)

## IMPLEMENTACION

Instalar Docker 
Instalar Git Bash
Instalar Visual Studio Code

Pasos previos a la instalación de Docker.

Aislar la red: Ejecuta la aplicación en una red Docker separada para evitar la comunicación con otras aplicaciones o el host. Para ello, utilizaremos la opción --network en el comando docker run para especificar la red.
Crear una red personalizada con el comando docker network create.

Limitar puertos expuestos: Unicamente dejaremos expuestos los puertos necesarios para el funcionamiento de la aplicación. Utilizaremos la opción -p : en el comando docker run para especificar los puertos. No exponer puertos innecesarios que podrían ser utilizados para ataques.

Utilizar la herramienta Snyk para escanear vulnerabilidades en aplicaciones Docker: Priorizar las vulnerabilidades críticas y tomar las medidas necesarias para corregirlas. Esto puede implicar actualizar dependencias, modificar configuraciones o reemplazar componentes vulnerables.

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
## SAST: Pruebas estáticas de seguridad de aplicaciones 

### Paso 1: Instalar Docker Bench Security
1. Clonar el repositorio de Docker Bench Security.
    ```bash
    git clone https://github.com/docker/docker-bench-security.git
    ```

2. Cambiar al directorio del proyecto clonado.
    ```bash
    cd docker-bench-security
    ```

3. Dar permisos de ejecución al script.
    ```bash
    chmod +x docker-bench-security.sh
    ```

### Paso 2: Ejecutar Docker Bench Security
Ejecuta el script para comenzar la auditoría de seguridad.
```bash
sudo ./docker-bench-security.sh
```

El script revisará la configuración de Docker según las recomendaciones del Center for Internet Security (CIS) y te proporcionará un informe detallado sobre posibles vulnerabilidades y mejoras de configuración.

### Paso 3: Interpretar los resultados
Después de ejecutar el script, verás una salida detallada con varias verificaciones y sus resultados. Cada verificación vendrá con una descripción y un estado que puede ser `PASS`, `WARN`, o `INFO`. Revisa estos resultados y ajusta tu configuración de Docker según las recomendaciones.

# Resultados del análisis de la aplicacion sin modificar parámetros

1. Linux Hosts Specific Configuration

    [WARN] 1.1.1 - Ensure a separate partition for containers has been created (Automated)
        Peligro: No tener una partición separada para los contenedores puede llevar a problemas de rendimiento y seguridad. Si un contenedor consume todo el espacio en disco, puede afectar al sistema operativo anfitrión y a otros contenedores.

    [WARN] 1.1.3 - Ensure auditing is configured for the Docker daemon (Automated)
        Peligro: No tener configurada la auditoría para el daemon de Docker puede dificultar la detección de actividades sospechosas o no autorizadas.

    [WARN] 1.1.4 - Ensure auditing is configured for Docker files and directories - /run/containerd (Automated)
        Peligro: Sin auditoría, no se pueden detectar modificaciones no autorizadas ni accesos indebidos a estos archivos críticos.

    [WARN] 1.1.5 - Ensure auditing is configured for Docker files and directories - /var/lib/docker (Automated)
        Peligro: La falta de auditoría en este directorio puede permitir que actividades maliciosas pasen desapercibidas.

    [WARN] 1.1.6 - Ensure auditing is configured for Docker files and directories - /etc/docker (Automated)
        Peligro: Este directorio contiene configuraciones críticas de Docker. Sin auditoría, los cambios no autorizados no se detectarán.

    [WARN] 1.1.7 - Ensure auditing is configured for Docker files and directories - docker.service (Automated)
        Peligro: La auditoría del servicio de Docker es crucial para detectar cambios en cómo se inicia y se gestiona Docker.

    [WARN] 1.1.9 - Ensure auditing is configured for Docker files and directories - docker.socket (Automated)
        Peligro: La auditoría del socket de Docker es importante para detectar accesos no autorizados.

    [WARN] 1.1.10 - Ensure auditing is configured for Docker files and directories - /etc/default/docker (Automated)
        Peligro: Este archivo contiene configuraciones predeterminadas para Docker. Sin auditoría, los cambios pueden comprometer la seguridad.

    [WARN] 1.1.11 - Ensure auditing is configured for Dockerfiles and directories - /etc/docker/daemon.json (Automated)
        Peligro: Este archivo contiene configuraciones del daemon de Docker. La falta de auditoría puede permitir configuraciones inseguras.

    [WARN] 1.1.12 - Ensure auditing is configured for Dockerfiles and directories - /usr/bin/docker-containerd (Automated)
        Peligro: La auditoría de este archivo binario es esencial para garantizar que no haya sido comprometido.

    [WARN] 1.1.13 - Ensure auditing is configured for Dockerfiles and directories - /usr/bin/docker-runc (Automated)
        Peligro: Similar al anterior, este archivo binario necesita auditoría para evitar compromisos de seguridad.

1.2 General Host Configuration

[WARN] 1.2.1 - Ensure a separate partition for containers has been created (Automated)
Peligro: Repetido del punto 1.1.1.

2. Docker Daemon Configuration

    [WARN] 2.1 - Ensure network traffic is restricted between containers on the default bridge (Automated)
        Peligro: Sin restricción del tráfico, los contenedores pueden comunicarse libremente, lo que puede facilitar la propagación de ataques.

    [WARN] 2.2 - Ensure the logging level is set to 'info' (Automated)
        Peligro: Configuraciones de logging menos detalladas pueden dificultar la detección y resolución de problemas.

    [WARN] 2.6 - Ensure that the --authorization-plugin parameter is not set to allow all (Manual)
        Peligro: Permitir que cualquier acción sea autorizada puede comprometer seriamente la seguridad del sistema.

3. Docker Daemon Configuration Files

    [WARN] 3.1 - Ensure that the Docker daemon's configuration file ownership is set to root:root (Automated)
        Peligro: Si el archivo de configuración no está protegido, puede ser modificado por usuarios no autorizados.

4. Container Images and Build Files

    [WARN] 4.1 - Ensure that a user for the container has been created (Automated)
        Peligro: Ejecutar contenedores como root puede aumentar los riesgos de seguridad en caso de compromiso.

5. Container Runtime

    [WARN] 5.1 - Ensure that, if applicable, an AppArmor profile is enabled (Automated)
        Peligro: Sin AppArmor, los contenedores tienen menos restricciones de seguridad.

    [WARN] 5.2 - Ensure that, if applicable, SELinux security options are set (Automated)
        Peligro: Similar a AppArmor, SELinux proporciona controles de seguridad adicionales que son importantes.

    [WARN] 5.9 - Ensure that the host's network namespace is not shared (Automated)
        Peligro: Compartir el namespace de red del anfitrión puede exponer el sistema a ataques desde los contenedores.

6. Docker Security Operations

    [WARN] 6.1 - Ensure that image sprawl is avoided (Manual)
	  Peligro: Tener demasiadas imágenes puede dificultar la gestión y aumentar los riesgos de seguridad.

    [WARN] 6.2 - Ensure that container sprawl is avoided (Manual)
        Peligro: Similar al anterior, demasiados contenedores pueden ser difíciles de gestionar y asegurar.
        
# Resultados del análisis de verificación de la aplicación con parámetros modificados.

[WARN] 4.1 - Ensure that a user for the container has been created (Automated):
        Antes: [WARN] * Running as root: sad_lehmann
        Ahora: [WARN] * Running as root: flamboyant_morse
	
 [WARN] 4.6 - Ensure that HEALTHCHECK instructions have been added to container images (Automated):
        Antes: [WARN] * No Healthcheck found: [getting-started-app:latest]
        Ahora: [WARN] * No Healthcheck found: [getting-started-app:latest]
        [WARN] * No Healthcheck found: e346052bbd7e
	
 [WARN] 5.3 - Ensure that, if applicable, SELinux security options are set (Automated):
        Antes: [WARN] * No SecurityOptions Found: sad_lehmann
        Ahora: [WARN] * No SecurityOptions Found: flamboyant_morse
	
 [WARN] 5.9 - Ensure that only needed ports are open on the container (Manual):
        Antes: [WARN] * Port in use: 3000 in sad_lehmann
        Ahora: [WARN] * Port in use: 3000 in flamboyant_morse
        [WARN] * Port in use: 8080 in flamboyant_morse
	
 [WARN] 5.11 - Ensure that the memory usage for containers is limited (Automated):
        Antes: [WARN] * Container running without memory restrictions: sad_lehmann
        Ahora: [WARN] * Container running without memory restrictions: flamboyant_morse
	
 [WARN] 5.12 - Ensure that CPU priority is set appropriately on containers (Automated):
        Antes: [WARN] * Container running without CPU restrictions: sad_lehmann
        Ahora: [WARN] * Container running without CPU restrictions: flamboyant_morse
	
 
[WARN] 5.13 - Ensure that the container's root filesystem is mounted as read only (Automated):
        Antes: [WARN] * Container running with root FS mounted R/W: sad_lehmann
        Ahora: [WARN] * Container running with root FS mounted R/W: flamboyant_morse
	
 [WARN] 5.14 - Ensure that incoming container traffic is bound to a specific host interface (Automated):
        Antes: [WARN] * Port being bound to wildcard IP: 0.0.0.0 in sad_lehmann
        Ahora: [WARN] * Port being bound to wildcard IP: 0.0.0.0 in flamboyant_morse
        [WARN] * Port being bound to wildcard IP: 0.0.0.0 in flamboyant_morse
	
 [INFO] 5.19 - Ensure that the default ulimit is overwritten at runtime if needed (Manual):
        Antes: [INFO] * Container no default ulimit override: sad_lehmann
        Ahora: [INFO] * Container no default ulimit override: flamboyant_morse
	
 [WARN] 5.26 - Ensure that the container is restricted from acquiring additional privileges (Automated):
        Antes: [WARN] * Privileges not restricted: sad_lehmann
        Ahora: [WARN] * Privileges not restricted: flamboyant_morse
	
 [WARN] 5.27 - Ensure that container health is checked at runtime (Automated):
        Antes: [WARN] * Health check not set: sad_lehmann
        Ahora: [WARN] * Health check not set: flamboyant_morse
	
 [WARN] 5.29 - Ensure that the PIDs cgroup limit is used (Automated):
        Antes: [WARN] * PIDs limit not set: sad_lehmann
        Ahora: [WARN] * PIDs limit not set: flamboyant_morse
	
 [INFO] 5.30 - Ensure that Docker's default bridge 'docker0' is not used (Manual):
        Antes: [INFO] * Container in docker0 network: sad_lehmann
        Ahora: [INFO] * Container in docker0 network: flamboyant_morse
	
 [INFO] 6.1 - Ensure that image sprawl is avoided (Manual):
        Antes: [INFO] * There are currently: 4 images
        Ahora: [INFO] * There are currently: 6 images
	
 [INFO] 6.2 - Ensure that container sprawl is avoided (Manual):
        Antes: [INFO] * There are currently a total of 6 containers, with 1 of them currently running
        Ahora: [INFO] * There are currently a total of 11 containers, with 1 of them currently running

Resumen de las Diferencias

* Cambios en Nombres de Contenedores: Los contenedores han cambiado de sad_lehmann a flamboyant_morse.
* Nuevas Advertencias de Puertos: Se han detectado puertos adicionales en uso (8080) y se han reportado más advertencias de puertos abiertos.
* Más Contenedores y Imágenes: El número de contenedores e imágenes ha aumentado en el sistema.
* Advertencias y Configuraciones Persistentes: Muchas advertencias persisten con los nuevos contenedores, indicando configuraciones subóptimas similares a las anteriores.

Acciones Recomendadas

* Configurar Usuarios No Root: Asegúrate de que los contenedores no se ejecuten como root.
* Añadir Health Checks: Implementa instrucciones HEALTHCHECK en tus Dockerfile
* Limitar Recursos: Establece límites de uso de memoria y CPU para los contenedores.
* Restringir Privilegios: Configura los contenedores para que no adquieran privilegios adicionales.
* Especificar Interfaces de Red: Asegúrate de que el tráfico de contenedores esté vinculado a interfaces de red específicas.

## DAST: Pruebas dinámicas de seguridad de aplicaciones

# Zed Attack Proxy (ZAP)
Zed Attack Proxy (ZAP) es un escaner de aplicaciones web de código abierto. Para la instalación de esta aplicación nos dirigiremos a el siguiente link:

* [zaproxy.org](https://www.zaproxy.org/)

![zap1](https://github.com/paserarra0/to-do/assets/156304388/635adec0-cc48-4cd4-a6a7-9f590912df12)

A continuación seleccionaremos el instalador de Linux ya que usaremos una máquina virtual Ubuntu 22.04

![zap2](https://github.com/paserarra0/to-do/assets/156304388/70ea8b39-7a15-4797-8831-f624ca47d297)

Una vez descargado el instalador, tendremos que instalar Java si no lo tenemos descargado. Lo podremos hacer con los siguientes comandos:
```
  sudo apt install default-jre
  sudo apt install default-jdk
```
Para ejecutar el instalador tendremos que cambiar los permisos de la aplicación con el siguiente comando:
```
  chmod o+x ZAP_2_15_0_unix.sh
```
Finalmente lanzaremos el instalador con:
```
  sudo ./ZAP_2_15_0_unix.sh
```
A continuación se lanzará la interfaz gráfica del instalador, solo tendremos que darle a "Next" hasta que finalice. Cuando termine la instalación se abrirá ZAP y veremos el menú principal.

![zap3](https://github.com/paserarra0/to-do/assets/156304388/383d98e9-4a74-48b1-bbc2-3d0a73d0f4eb)

![zap4](https://github.com/paserarra0/to-do/assets/156304388/bc8fec33-b1f9-4928-8533-ff45c713bc88)

Para lanzar un análisis automático le daremos al icono que se señala y completaremos el campo de URL con la dirección de la aplicación to-do.

![zap5](https://github.com/paserarra0/to-do/assets/156304388/7f4cda68-9dab-4a92-86c3-f45a44097a6d)

![zap6](https://github.com/paserarra0/to-do/assets/156304388/ed757189-8553-483f-be27-def7b79b75e2)

Podremos ver las alertas encontradas con sus respectivos detalles.

![zap7](https://github.com/paserarra0/to-do/assets/156304388/9353338f-e20a-47b2-91c2-52f5ffe7d682)

### Resultados del análisis de la aplicacion:

**CSP: Wildcard Directive (2)**: la política de seguridad de contenido (CSP) utiliza comodines (wildcards) como '*'. Esto puede permitir la ejecución de scripts y recursos no autorizados. Para resolver esta alerta se podría restringir el uso de comodines en tu CSP y definir fuentes específicas de contenido. 

**Content Security Policy (CSP) Header Not Set**: no se ha configurado la cabecera CSP, lo que permite la carga de scripts y recursos desde cualquier origen. Se debería configurar una política CSP adecuada que especifique las fuentes permitidas para scripts, estilos, imágenes, etc.

**Missing Anti-clickjacking Header**: Falta la cabecera X-Frame-Options, lo que permite que tu sitio web sea embebido en un iframe por otros sitios, facilitando ataques de clickjacking.

**Server Leaks Information via "X-Powered-By" HTTP Response Header Field(s) (11)**: la cabecera X-Powered-By revela información sobre el servidor, como la tecnología y la versión utilizada, facilitando ataques específicos.

**X-Content-Type-Options Header Missing (9)**: falta la cabecera X-Content-Type-Options, lo que permite a los navegadores interpretar los archivos de manera incorrecta y potencialmente peligrosa.

**Information Disclosure - Suspicious Comments (16)**: se han encontrado comentarios sospechosos en el código fuente que podrían revelar información sensible o puntos de entrada para ataques.

**Modern Web Application**: esta es una categoría general que ZAP utiliza para indicar que la aplicación web tiene características modernas. No es necesariamente una vulnerabilidad.



## RASP: Protección del lado del servidor en tiempo real

### Paso 1: Instalar Trivy

```bash
sudo apt-get install wget apt-transport-https gnupg lsb-release
wget -qO - https://aquasecurity.github.io/trivy-repo/deb/public.key | sudo apt-key add -
echo deb https://aquasecurity.github.io/trivy-repo/deb $(lsb_release -sc) main | sudo tee -a /etc/apt/sources.list.d/trivy.list
sudo apt-get update
sudo apt-get install trivy
```
Reemplazar [YOUR_CACHE_DIR] con el directorio de caché de la máquina.

```bash
docker pull aquasec/trivy:0.17.2
```

### Paso 2: Scripts para exploración de caché

Borrar cachés

```bash
$ trivy image --clear-cache
```
Resultados 
```bash
2024-05-19T15:13:26.209+0200    INFO    Reopening vulnerability DB
2024-05-19T15:13:26.209+0200    INFO    Removing image caches...
```
Directorio de caché

Especificar donde se almanece el caché
```bash
$ trivy --cache-dir /tmp/trivy/ image python:3.4-alpine3.9
```

Servidor de caché 

Esta función puede cambiar sin preservar la compatibilidad con versiones anteriores. Esta opción es útil para el modo cliente/servidor.

```bash
$ trivy server --cache-backend redis://localhost:6379
```

# Resultados del análisis de la aplicacion

* Capacidad para Borrar Cachés: Trivy proporciona un comando específico (trivy image --clear-cache) para borrar los cachés de imágenes, lo cual es útil para mantener el sistema limpio y asegurar que los escaneos futuros utilicen datos actualizados.
* Personalización del Directorio de Caché: Es posible especificar un directorio personalizado para el almacenamiento del caché mediante la opción --cache-dir. Esto ofrece flexibilidad para almacenar el caché en una ubicación distinta a la predeterminada, lo cual puede ser útil en sistemas con diferentes configuraciones de almacenamiento.
* Uso de un Servidor de Caché: Trivy soporta la configuración de un servidor de caché externo, como Redis, a través de la opción --cache-backend. Esta funcionalidad es particularmente valiosa en entornos de cliente/servidor, donde varios clientes pueden beneficiarse de un caché centralizado, mejorando el rendimiento y la eficiencia de los escaneos. Se menciona que esta funcionalidad puede cambiar sin mantener compatibilidad con versiones anteriores, lo que sugiere la importancia de revisar las actualizaciones de la herramienta para asegurar la compatibilidad.
* Mejora en la Gestión y Rendimiento: Las opciones para borrar el caché, personalizar el directorio de almacenamiento, y utilizar un servidor de caché contribuyen a una mejor gestión de los recursos y optimización del rendimiento de Trivy. Esto permite adaptarse a diferentes entornos y necesidades específicas de los usuarios


   
## CONCLUSIONES

* Se reconoce la importancia del Ciclo de Vida de Desarrollo de Software (SDLC) para garantizar un desarrollo seguro desde el inicio del proyecto hasta su despliegue y mantenimiento.
* Se reconoce la importancia del DevSecOps para desarrollar de forma segura el Software, estableciento un entorno seguro en el proceso end-to-end a través de pruebas y monitoreo. 
* Se ha identificado y seleccionado una aplicacion existente (TO-DO) como referencia y se ha creado una estructura de proyecto que incluye los archivos y herramientas necesarios. 
* Se han desarrollado consideraciones de seguridad utilizando el SDLC, aplicando tareas de seguridad en cada etapa.
* Se han tenido en cuenta las herramientas creadas por los integrantes del grupo, así como sus aplicativos de seguridad y sus posibles vulnerabilidades. 
* Se ha seguido un proceso paso a paso para implementar la aplicacion utilizando Docker, destacando la importancia de garantizar la seguridad en cada paso. 
* Se han utilizado diversas herramientas de seguridad, como Git Bash, Visual Studio Code y Docker Playground, para garantizar la seguridad durante el desarrollo y despliegue de la aplicacion.
