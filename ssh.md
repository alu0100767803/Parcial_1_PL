Explique como se generan las claves privada y pública
* `>$ ssh-keygen`
* Después de ejecutar el comando solicita el nombre de archivo para guardar la clave, dejar en blanco para utilizar el archivo por defecto.
* Posteriormente solicita dos veces la clave, dejar en blanco para no protegar los archivos con clave.

Como se publica una clave?
* Manualmente, añadiendo la clave pública del cliente en /.ssh/authorezed_keys del servidor, o
* `>$ ssh-copy-id usarname@host.com`

Indique como se puede configurar el cliente SSH para simplificar la conexión
* Generando una entrada en el fichero config
~~~
host alias
  Hostname example.com
  Username username
  IdentityFile /ruta de la clave privada
~~~  
¿Cómo puedo ejecutar un script en una máquina accesible via SSH?

* `ssh hostAlias node app.js`
