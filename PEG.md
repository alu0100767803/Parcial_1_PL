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
   ```

   se debería traducir como:

   ```
   var b = 5;
   var c = 2;
   var a = 4*b+c;
   b+c+a
   ```

   ````
   start
       = s:semicolon{return s;}
       
   semicolon
       = a:assign op:SEMICOLON sc:semicolon{return a + op + "\n" + sc;}
           /assign
           
   assign
       = id:ID eq:EQUAL a:additive{ return "var " + id + " " + eq + " " + a;}
           /additive
       
   additive
       = m:multiplicative op:ADDOP a:additive {return m + op + a;}
           /multiplicative
           
   multiplicative
       = p:primary op:MULOP m:multiplicative {return p + op + m;}
           /parent

   parent
       = primary 
           /l:LEFTPAR a:additive r:RIGHTPAR{return l + a + r;}
       
           
   primary
       =NUMBER
       / ID

   _ = $[ \n\t\r]*

   EQUAL = _"="_{return "=";}
   SEMICOLON = _";"_{return ";";}
   ADDOP = PLUS / MINUS
   MULOP = MULT / DIV
   PLUS = _"+"_{return "+";}
   MINUS = _"-"_{return "-";}
   MULT = _"*"_{return "*";}
   DIV = _"/"_{return "/";}
   NUMBER = _ number:$[0-9]+ _ {return parseInt(number, 10);}
   ID = _ id:$[a-z]+ _ {return id;}
   LEFTPAR = _"("_
   RIGHTPAR = _")"_
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

7. Escriba un peg que reconozca el lenguaje \{ a^nb^nc^n / n \ge 1 \}{anbncn/n≥1}

   ```
   S = &(A 'c') 'a'+ B:B !.  { return B; }
   A = 'a' A:A? 'b' { if (A) { return A+1; } else return 1; }
   B = 'b' B:B? 'c' { if (B) { return B+1; } else return 1; }
   ```

8. Indique como es la estructura de tabla de símbolos de un compilador y como se construye. Explique como el anidamiento de las tablas de símbolos refleja el ámbito de las variables

   ```

   ```

9. Indique como se hace el análisis de tipos en un compilador mediante la decoración del árbol con el atributo `tipo`. Señale las diferentes formas en la que se pueden resolver las cincompatibilidades de tipos

   ````

   ````

   ​
   10.Ejercicio del examen parcial.
   Escribe un pegs que traduzca:

 ````
	b -> 5:
	c -> 2:
	a -> 4*b+c:
	b+c+a:
 ````
En lenguaje Javascript:
````
	let $a,$b,$c;
	$b = 5;
	$c = 2;
	$a = 4*$b*$c;
	$b+$c+$a;
````
````
{
let variables = []
}

start
    = c:colons{return "let " + variables.join() + "\n" + c;}
    
colons
    = a:assign COLONS c:colons{return a + ";\n" + c;}
        /a:assign COLONS{return a + ";";}
        
assign
    = id:ID ARROW a:additive{ variables.push(id); return id + " = " + a;}
        /additive
    
additive
    = m:multiplicative op:ADDOP a:additive {return m + op + a;}
        /multiplicative
        
multiplicative
    = p:primary op:MULOP m:multiplicative {return p + op + m;}
        /parent

parent
    = primary 
        /LEFTPAR additive RIGHTPAR
    
        
primary
    =NUMBER
    / ID

_ = $[ \n\t\r]*

ARROW = _"->"_;
COLONS = _":"_;
ADDOP = PLUS / MINUS
MULOP = MULT / DIV
PLUS = _"+"_{return "+";}
MINUS = _"-"_{return "-";}
MULT = _"*"_{return "*";}
DIV = _"/"_{return "/";}
NUMBER = _ number:$[0-9]+ _ {return parseInt(number, 10);}
ID = _ id:$[a-z]+ _ {return "$" + id;}
LEFTPAR = _"("_
RIGHTPAR = _")"_
````

