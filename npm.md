¿Con que comando creo el fichero package.json?
* npm init
Explique en consiste el versionado semántico/semantic versioning. ¿Cual es el nombre en inglés de los tres números de version? ¿Como cambian?
* Es un sistema de numeración de versiones formado por tres núnmeros, X.Y.Z, en el que cada número cambian en función de las modificaciones de el código.
* X = major, Y = minor, Z = Patch
* Major, cambios importantes en el código, en el que se pueden generar incompatibilidades con versiones anteriores.
* Minor, cambio de algunas características o adición de nuevas características, con retrocompatibilidad.
* Patch, arreglo de bugs, se mantiene compatibilidad.

¿Que se guarda en el campo "dependencies": {} de package.json?
* Las dependencias de producción del código, es decir, las dependencias que son necesarias cuando se utiliza el código desarrollado.

¿Que opción debo añadir al comando npm install para que la librería instalada se añada como dependencia en el fichero package.json?
* -S --save para dependencia de producción

¿Que se guarda en el campo "devDependencies": {} de package.json?
* Las dependencias de desarrollo del paquete.

¿Que opción debo añadir al comando npm install para que la librería instalada se añada como "devDependencies" en el fichero package.json?
* -D --save-dev para dependencia de desarrollo

Explique que significan en los objetos que describen las dependencias dentro package.json las siguientes notaciones:
* **\*** cualquier versión
* **latest** la última versión.

¿Cual es la salida? ¿Como actúa el operador ~?
~~~
> var semver = require('semver')
undefined
> semver.toComparators('~1.2.3')
[ [ '>=1.2.3', '<1.3.0' ] ]
~~~
* Versiones superiores que solo cambien en el patch

¿Cual es la salida? ¿Como actúa el operador ^?
~~~
> var semver = require('semver')
undefined
> semver.toComparators('^1.2.3')
[ [ '>=1.2.3', '<2.0.0' ] ]
~~~
* Versiones superiores que solo cambien en el patch y en minor

¿Cuales son los pasos para escribir y publicar un paquete npm?
* git init
* git remote add .....
* npm init
* touch .npmignore (añadir los ficheros a ignorar, node_modules.........)
* touch .gitignore (añadir los ficheros a ignorar, node_modules, ..........)
* crear código
* crear cuenta en npm
* npm login
* npm publish

¿Cómo instalo una versión anterior de un package npm?
* `npm install <package>@<version>`

¿Cómo encuentro la versión de un paquete NodeJs instalado?
* node --version
