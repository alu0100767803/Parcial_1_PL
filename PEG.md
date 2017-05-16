1. ¿Que opción debemos pasar a pegjspara que admita que las acciones semánticas se especifiquen en CoffeeScript?

   ````
   pegjs --plugin pegjs-coffe-plugin simple.pegjs
   ````

   ​

2. Escriba en PEGJS un traductor de expresiones aritméticas a postfijo. Una expresión como a = 4*b+c se debe traducir por 4 b * c + &a =

   ````
   {  

     const util = require('util');

     function reduce(left, right) {
       var sum = left;
       right.forEach((r,_) => {
         let [op, num] = r; // node --harmony_destructuring
          sum += ` ${num} ${op}`;
       });
     
       return sum;
     }
     
     function prueba(left, right){
       var sum = left;
       console.log(right);
       sum += ` $${right[0]} ${right[1]}`;
       return sum;
     }
   }

   start = right:(ID ASSIGN) left:sum         {return prueba(left, right);}            
           / sum
   sum     = left:product right:($[+-] product)* { return reduce(left, right); }
   product = left:value   right:($[*/] value)*   { return reduce(left, right); }
   value   = number:NUMBER                       { return number; }
           / id:ID                               { return id;}
           / '(' sum:sum ')'                     { return sum; }

   NUMBER = number:$[0-9]+ {return number;}
   ID = id:$([a-z_]i$([a-z0-9_]i*)) {return id;}
   ASSIGN = "=" {return "=";}
   ````

3. Escriba un PEGJS que traduzca secuencias de expresiones aritméticas separadas por puntos y comas a JavaScript. Una secuencia de expresiones como

   ```
   b = 5;
   c = 2;
   a = 4*b+c;
   b+c+a
   Copy
   ```

   se debería traducir como:

   ```
   var b = 5;
   var c = 2;
   var a = 4*b+c;
   b+c+a
   ```

   ````

   ````

4. Escriba un peg que reconozca las sentencias `if then ...` e `if then ... else ...` asociando cada `else` con el `if` mas cercano`if a then if b then o else o`

````
start = S
S = IF c:C THEN s1:S ELSE s2:S {return ['ifthenelse', C, s1, s2];}
	/ IF c:C then s:S {return ['ifthen', c s];}
	/ O

_ = [ \t\r\n]+
C = "c" {return "c";}
O = "o" {return "o";
IF = "if"
ELSE = "else"
THEN = "then"
````

5. Explique como se le puede pasar información al objeto Parser generado por PEG.js

````
Ejecutando el método parse y pasándole la información como parámetro
por ejemplo var r = PEG.parse(input);
````

6. Escriba un peg que reconozca los comentarios Pascal anidados

   ````
   start = 
   pascal = comment
   		/  (!Begin !End char:.)          { return char;}
   comment = BEGIN chars:$T* END {return "Comentario: "+chars;}

   BEGIN = "(*"
   END = "*)"
   ````

   ​