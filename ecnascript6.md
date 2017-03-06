https://carlosazaustre.es/blog/ecmascript-6-el-nuevo-estandar-de-javascript/



Observemos este ejemplo:
~~~
class Contact {
  constructor(name, email, button) {
    this.name = name;
    this.email = email;

    button.onclick = function(event) {
      sendEmail(this.email);
    }
  }
}
~~~
¿Cuanto vale this en la línea 6?
¿Como podemos reescribir este código en ECMA6 para que this refiera al objeto Contact?
¿Que se entiende por Hoisting en JS? ¿Que efectos indeseables conlleva?
Es el proceso por el cual todas las declaraciones de variables son elevada al principio de su scope, esto produce efectos indeceables porque se eleva su declaración y no su asignación, lo que puede hacer que hagamos uso de una variable con un valor que no es el esperado.

~~~
function ejemplo1(){
alert("Valor de x: " + x );
var x = 7;
alert("Valor de x: " + x );
}



function ejemplo1(){
var x;
alert("Valor de x: " + x );
x=7;
alert("Valor de x: " + x );
}
~~~


¿Como se soluciona en ECMA6?


* Ni idea
