https://carlosazaustre.es/blog/ecmascript-6-el-nuevo-estandar-de-javascript/



Observemos este ejemplo:
~~~javascript
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
* This apunta a la función en la que se llama, en este caso si la fucnción declarada en la linea 5 no define email, su valor es undefined.

¿Como podemos reescribir este código en ECMA6 para que this refiera al objeto Contact?
~~~javascript
class Contact {
  constructor(name, email, button) {
    this.name = name;
    this.email = email;

    button.onclick = event => {sendEmail(this.email);}
  }
}
~~~

¿Que se entiende por Hoisting en JS? ¿Que efectos indeseables conlleva?
* Es el proceso por el cual todas las declaraciones de variables son elevada al principio de su scope, esto produce efectos indeceables porque se eleva su declaración y no su asignación, lo que puede hacer que hagamos uso de una variable con un valor que no es el esperado.

~~~javascript
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
* Si la variable es usada antes de su declaración no devuelve undefined, sino reference error, ya que la variable es conocida, pero no se le ha asignado un valor.
* A esta zona en la que la variable está creada pero indefinida se le denomina temporal dead zone.
* [Explicación punto 9.4](http://exploringjs.com/es6/ch_variables.html#sec_temporal-dead-zone)

~~~javascript
let tmp = true;
if (true) { // enter new scope, TDZ starts
    // Uninitialized binding for `tmp` is created
    console.log(tmp); // ReferenceError

    let tmp; // TDZ ends, `tmp` is initialized with `undefined`
    console.log(tmp); // undefined

    tmp = 123;
    console.log(tmp); // 123
}
console.log(tmp); // true
~~~
