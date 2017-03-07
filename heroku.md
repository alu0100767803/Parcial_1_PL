Una vez instalado el Heroku cli nos debemos autenticar en heroku con el cliente. ¿Cual es el comando para autenticarnos?
 * heroku login

¿Cual es el comando para crear nuestra aplicación en Heroku (suponemos que ya esta bajo el control de git? ¿Qué remoto tendremos definido después de crear nuestra aplicación en Heroku?
* heroku create.
* heroku

¿Cual es el comando para desplegar nuestra aplicación en Heroku?
* git add .
* git commit -m "mensaje"
* git push heroku master

Si la versión que queremos publicar en heroku no está en la rama master sino que está en la rama tutu ¿Como debemos modificar el comando anterior?
* git push heroku ramalocal:ramaremota
* git push heroku tutu:master

¿Con que comando puedo abrir una ventana en el navegador que visite la aplicación desplegada? ¿Que formato tiene la URL para nuestra aplicación?
* heroku open

¿Con que comando puedo ver los logs de la aplicación desplegada?
* heroku logs

¿Como se debe llamar el fichero en el que explicito que comando debe usarse para arrancar nuestra aplicación en Heroku?
* Procfile

Heroku se percata que nuestra aplicación es una aplicación desarrollada con Node.js por la presencia de un cierto fichero. ¿De que fichero estamos hablando?
* package.json

¿Cual es la mejor forma de ejecutar en local una aplicación express.js que va a ser desplegada en Heroku?
* heroku local

Explique los pasos para desplegar una aplicación en Heroku
* Heroku create.
* Escribir aplicación.
* Heroku local para probarla en local.
* crar un fichero procfile que contenga la indicación de que fichero ejecutar p.e: web: node app.js
* git add .
* git commit -m "mensaje"
* git push heroku master.

Explique como resolver los problemas que pueden surgir cuando la aplicación desplegada en Heroku no funciona correctamente
* consutar fichero de log con heroku logs.
* depurar la app en local corrigiendo los posibles errores y subirla de nuevo  

¿Como consulto el token para hacer uso de la API de Heroku?
* heroku auth:token

¿Cómo creo una app en Heroku usando la API de Heroku?

* Véase
* With a source tarball, which contains an app.json, call the https://api.heroku.com/app-setups endpoint to setup the app.json enabled application on Heroku. The request body must contain a source URL that points to the tarball of your application’s source code.
Let’s use cURL to call the app-setups endpoint:

~~~sh
$ curl -n -X POST https://api.heroku.com/app-setups \
-H "Content-Type:application/json" \
-H "Accept:application/vnd.heroku+json; version=3" \
-d '{"source_blob": { "url":"https://github.com/heroku/ruby-rails-sample/tarball/master/"} }'

~~~

Explique los pasos para publicar un libro GitBook en Heroku
* crear el libro en markdown con el formato y la estructura que requiere GitBook.
* hacer un gitbook build para construir el html del libro.
* crear un servidor que sirva los ficheros estáticos del libro.
* crear el procfile que ejecute el servidor.
* git init
* heroku create
* git add .
* git commit -m "mensaje"
* git push heroku master
