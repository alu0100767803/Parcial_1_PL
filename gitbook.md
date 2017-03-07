¿Cómo se escribe en GitBook esta fórmula?
* \$\$x=\frac{1+y}{1+2z^2}\$\$

¿Como se escribe un código JavaScript de manera que se muestre con syntax highlingting?

>\`\`\`javaScript

var a = 3;
var b = b+1;

\`\`\`

```javaScript
var a = 3;
var b = b+1;
```
¿Como se escribe un bloque de cita blokquote?

\> Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad

> Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim

¿Que pasos debo dar para insertar un vídeo de YouTube en mi libro GitBook?

* Añadir el script correspondiente a book.json
* En el text añadir `{% youtube %}enlace al video {% endyoutube %}`

Escriba el código MD para producir una tabla como esta:

| First Header | Second Header |
| -- | -- |
| Content Cell | Content Cell |
| Content Cell | Content Cell |

\| First Header | Second Header |
\| -- | -- |
\| Content Cell | Content Cell |
\| Content Cell | Content Cell |

¿Donde puedo encontrar la URL del repositorio en GitBook del libro?
* book.json

Explique los pasos para publicar un libro GitBook en GitHub usando las gh-pages de GitHub manualmente
* Escribir el libro en markdown con la estrutura requerida por gitbook
* Hacer gibook build del libro para generar los html
* Subir los html generados a la rama gh-pages del repositorio en github

¿Que atributo debo de poner en book.json para alojar los Markdown del libro en un directorio distinto del raiz?
* Se debe modificar el atributo root indicando la ruta del directorio respecto al directorio raiz.
