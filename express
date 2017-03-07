Escriba un servidor que sirva ficheros estáticos desde el directorio /public
~~~javascript
var express = require('express');
var app = express();
var path = require('path');

app.set('port', (process.env.PORT || 5000));

app.get('/', function(pet, res){
  res.sendfile(__dirname + '/public/index.html');
});

app.use(express.static(path.resolve('public')));
app.listen(app.get('port'));
~~~

El servidor deberá responder a requests GET en las rutas /user/nombredeusuario (donde nombredeusuario varía) con una página que diga Hola nombredeusuario usando el método renderdel objeto response

* La página se elaborara con una vista que debe estar en el directorio views/ usando el motor de vistas ejs

* La página elaborada en la respuesta tendrá un tag img referenciando a una imagen que está en public/

~~~javascript
app.set('views', path.join(__dirname, 'views'));
app.set('view engine', 'ejs');
app.get('/users/:username', function(req, res){
  var username = req.params.username;
  res.render("user",{name: username});
}),

~~~

~~~html
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <title>Users Page</title>
</head>
<body>
  <p>
    Hola <%= name %>
    <img src="/Tigre.png" alt="" />
  </p>

</body>
</html>
~~~
Escriba un middleware que intercepte en las rutas /user/nombredeusuario y que vuelque en la consola información sobre el request: (por ejemplo los atributos method, path, etc.)
~~~javascript
var express = require('express');
var path = require('path');
var route = express.Router();

route.get('/:username', function(req, res){
  console.log(req.method);
  console.log(req.path);
  console.log(req.body);
}),
module.exports = route;
~~~

Explique como se puede aislar el código anterior en un fichero routes/user.js que sea cargado desde el programa principal
~~~javascript
var express = require('express');
var path = require('path');
var route = express.Router();

route.get('/:username', function(req, res){
  console.log(req.method);
  console.log(req.path);
  console.log(req.body);
}),
module.exports = route;
~~~
Explique que hay que hacer para desplegar la aplicación en Heroku
* añadir un Procfile con el contenido web: app.js, donde app.js es nuestro servidor.
* añadir un packaje.json, para que heroku identifique que nuestra app es node
* subir el codigo a heroku
  * git add .
  * git commit -m "subiendo a heroku"
  * git push heroku master
* heroku open para abrir en el navegador

Explique que hay que hacer para desplegar la aplicación en la máquina virtual del iaas
* Subir los fichero al servidor en el IAAS.
* mediante una sesión ssh arrancar ejecutar el servidor en la máquina del IAAS
  * ssh prolen
  * cd nuestroproyecto
  * node app.js, donde app.js es nuestra app node.
  
