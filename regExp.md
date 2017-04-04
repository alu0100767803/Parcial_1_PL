1. Escriba expresiones regulares que casen con las siguientes especificaciones:
   1. car and cat
   2. pop and prop
   3. ferret, ferry, and ferrari
   4. Any word ending in ious
   5. A whitespace character followed by a dot, comma, colon, or semicolon
   6. A word longer than six letters
   7. A word without the letter e

```
	1. /ca[rt]/
	2. /pr?op/
	3. /ferr[et|y|ari]/
	4. /\w*ious\b/
	5. /\s[.,:;]/
	6. /\w{7,}/
	7. /\b[a-df-z]+\b/
```



2. Escriba una expresión regular que reconozca las cadenas de doble comillas. Debe permitir la presencia de comillas y caracteres escapados

   ````
   /"(\\.|[^\\"])*"/g
   ````

   ​

3. Escriba una expresión regular que reconozca los números en punto flotante (por ejemplo `-2.3e-1`, `-3e2`, `23`, `3.2`). numbers = /^ ... $/, matching exacto

   ````\b\d+(\.\d*)?([eE][+-]?\d+)?\b
   /[+-]?\b\d+(\.\d*)?([eE][+-]?\d+)?\b/g
   ````

4. Escriba una expresión regular que case con los números no primos expresados en unario. Pruebe con `1111`, `111`, `111111`, `1111111`, ./..

   ````
   /^1?$|^(11+?)\1+$/
   ````

5. Escriba una expresión regular que case con los comentarios JavaScript.

   ```g
   /\/\/.*|\/[*](.|\n)*?[*]\//g
   ```

6. Escriba una expresión JavaScript que permita reemplazar todas las

7. Rellene las partes que faltan:

```
> re = /d(b+)(d)/ig
/d(b+)(d)/gi
> z = "dBdxdbbdzdbd"
'dBdxdbbdzdbd'
> result = re.exec(z)
[ 'dBd', B, d, index: 0, input: 'dBdxdbbdzdbd' ]
> re.lastIndex
3
> result = re.exec(z)
[ dbbd, bb, d, index: 4, input: 'dBdxdbbdzdbd' ]
> re.lastIndex
8
> result = re.exec(z)
[ dbd, b, d, index: 9, input: 'dBdxdbbdzdbd' ]
> re.lastIndex
12
> result = re.exec(z)
null
```

1. Escriba la expresión regular `r` para que produzca el resultado final:

```
> x = "hello"
> r = /l(?=o)/
> z = r.exec(x)
[ 'l', index: 3, input: 'hello' ]
```

1. Rellene el valor que falta:

```
> z = "dBdDBBD"
> re = /d(b+)(d)/ig
> re.lastIndex = 3
> result = re.exec(z)
[ 'DBBD',
  'BB',
  'D',
  index: 3,
  input: 'dBdDBBD' ]
```

1. Conteste:

   1. Explique que hace el siguiente fragmento de código:

      ```
      > RegExp.prototype.bexec = function(str) {
      ...   var i = this.lastIndex;
      ...   var m = this.exec(str);
      ...   if (m && m.index == i) return m;
      ...   return null;
      ... }
      [Function]
      ```

   2. Rellene las salidas que faltan:

```
> re = /d(b+)(d)/ig
/d(b+)(d)/gi
> z = "dBdXXXXDBBD"
'dBdXXXXDBBD'
> re.lastIndex = 3
> re.bexec(z)
null
> re.lastIndex = 7
> re.bexec(z)
['DBBD','BB','D', index: 7, input: 'dBdXXXXDBBD']
```

1. Escriba una expresión JavaScript que permita reemplazar todas las apariciones de palabras consecutivas repetidas (como `hello hello`) por una sóla aparición de la misma

   ````
   str.replace(/(.)(?=.+\1)/, "")
   ````

   ​

2. ¿Cual es la salida?

   ```
   > "bb".match(/b|bb/)
   ['b', index: 0, input: 'bb']

   > "bb".match(/bb|b/)
   ['bb', index: 0, input: 'bb']
   ```

   Justifique su respuesta.

````En el primer match casa sólo la &#39;b&#39; dado que en la expresión regular hemos puesto primero la &#39;b&#39; a la &#39;bb&#39; por tanto va a casar con la primera &#39;b&#39; de la cadena y no comprobará más, en el segundo match pasa lo mismo solo que con &#39;bb&#39;.
En el primer match casa sólo la 'b' dado que en la expresión regular hemos puesto primero la 'b' a la 'bb' por tanto va a casar con la primera 'b' de la cadena y no comprobará más, en el segundo match pasa lo mismo solo que con 'bb'.
````

1. El siguiente fragmento de código tiene por objetivo escapar las entidades HTML para que no sean intérpretadas como código HTML. Rellene las partes que faltan.

```
var entityMap = {
    "&": "&amp;",
    "<": "&lt;",
    ">": "&gt;",
    '"': '&quot;',
    "'": '&#39;',
    "/": '&#x2F;'
  };

function escapeHtml(string) {
  return String(string).replace(/[&"'<>\/]/g, function (s) {
    return entityMap[s];
  });
```

1. Se quiere poner un espacio en blanco después de la aparición de cada coma:

```
> x = "a,b,c,1,2,d, e,f"
'a,b,c,1,2,d, e,f'
> x.replace(/\b(\w),\b/g,"$1, ")
'a, b, c, 1, 2, d,  e, f'
```

Se pide que si hay ya un espacio después de la coma, no se duplique.

2. Se pide una expresión regular que case con expresiones del tipo `identifier = number` y retorne con cada paréntesis el identificador y el número. Pruebe con `h = 4`, `temp = 5.6`, `x23= -2.3e1` y `z += 3`

   ````
   /([a-zA-Z_]\w*)\s*[+*\/%-]?=\s*([+-]?\b\d+(\.\d*)?([eE][+-]?\d+)?)\b/g
   ````

3. Imagine you have written a story and used single quotation marks throughout to mark pieces of dialogue. Now you want to replace all the dialogue quotes with double quotes, while keeping the single quotes used in contractions like *aren’t*. Think of a pattern that distinguishes these two kinds of quote usage and craft a call to the replace method that does the proper replacement.

```
var text = "'I'm the cook,' he said, 'it's my job.'";
// Change this call.
var result = text.replace(/(^|\W)'|'(\W|$)/g, '$1"');
console.log(result);
var expected = `"I'm the cook," he said, "it's my job."`;
if (expected === result) console.log("OK")
else console.log("ERROR!");
```



