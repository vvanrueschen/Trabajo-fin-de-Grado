# TFG -- Aplicación para la gestión de Docker con Framework para la generación automatica de APIs
El objetivo es desarrollar una aplicación que facilite a un programador la creación de un entorno para un nuevo proyecto que ya contenga todos los prerrequisitos necesarios para su proyecto y que además incluya un servidor API generado automáticamente a través del cual se pueda acceder a los respectivos componentes.
Por ejemplo, si el programador sabe desde el principio que su aplicación debe tener una base de datos y necesita un determinado framework para el lenguaje que va a utilizar, debería poder seleccionarlo simplemente a través de una interfaz de usuario y entonces se crearía automáticamente una entorno con estos requisitos.
La provisión de los distintos servicios se hará a través de Docker, ya que la combinación de imágenes (por ejemplo, distribución Linux + MySQL) hace que sea relativamente sencillo crear un entorno con todas las herramientas necesarias.
Aunque ya existe una interfaz de usuario para Docker llamada Docker Desktop, no es posible montar una imagen simplemente haciendo clic en las funciones deseadas. Para ello, hay que crear manualmente un Dockerfile o un archivo Docker-compose.
Para simplificar este proceso y añadir las características adicionales mencionadas anteriormente, se necesitan dos aplicaciones que juntas forman un sistema de gestión para Docker:
- Aplicación web como el interfaz de usuario para la gestión de contenedores docker (ASP.Net Core Web App)
  - Muestra contenedores y los imágenes de ellos
  - Ofrece un menú para crear nuevas imágenes y contenedores
  - El usuario sólo debe seleccionar sus funciones deseadas a traves de un formulario y la aplicación crea automáticamente el Dockerfile (docker compose) y los archivos de configuración necesarios para construir el imagen.
- Aplicación que comunica con los servidores de docker y kubernetes para aplicar los comandos de la aplicación web
  - Tiene una base de datos (Mongodb) in que se almacena los datos del usuario y informaciones sobre los servidores y imagenes ofrecidos
  - Accesible por un REST-API
  - Por este API también se podría enviar ficheros para crear un imagen incluyendo estos ficheros
  - Utiliza el API del docker-engine para comunicar con sol servidores
  - Debería generar automáticamente una API de Python a través de la cual se pueda acceder a, por ejemplo, un base de datos.
  - Para una imagen generada, también debería prepararse automáticamente un script a través del cual se pueda transferir el nuevo estado a, por ejemplo, Dockerhub cuando se realicen cambios. (CI/CD)

[Wiki Link](https://github.com/vvanrueschen/Trabajo-fin-de-Grado/wiki)
