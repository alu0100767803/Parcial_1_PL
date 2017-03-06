Explique las diversas formas de asociar un web site con un repo

* Publicando en la rama gh-pages de cualquier repo los archivos html de la página que se quiere publicar. https://usergithub.github.io/nombredelrepo
* Seleccionando la rama master de cualquier repo como origin de los archivos para la página y subiendo a ella los archivos html.
* Seleccionando la carpeta docs/ de la rama master de cualquier repo como origin de los archivos para la página y subiendo a ella los archivos html.

Explique como se asocia un website en GitHub con el usuario o la organización
* Publicando los html en la rama master de un repo con el mismo nombre que el nombre de usario de la cuenta https://usergithub.github.io

Explique como funcionan los

* issues: son avisos que se pueden poner en un repo para que el resto de los miembros del equipo puedan ver que se ha identificado un error y debe ser corregido, los issues pueden ser asigandos a una persona en concreto o ser abiertos, además se puede modificar su estado para indicar que está resuelto.
* las labels o etiquetas es un código de colores que permite distinger entre varios tipos de issues (urgentes, mejoras, resueltos)
* milestones, son hitos que se pueden marcar en los issues
* assignee, es un campo del issue mediante el cual puede ser asignado a una persona
* las @mentions se generan escribiendo dentro del issue @username para nombrar a otro usuario u organización dentro de github
* las referencias a issues, son referncias a issues anteriores y se generan intrudiciendo en el texto el #numero_del_issue dentro del texto del issue

¿Como se configura la recepción de notificaciones en GitHub?
* Settings/notifications

¿Que dos tipos de formas hay de recibir las notificaciones?
* email
* web

¿Que ocurre si en un mensaje de commit lo prefijamos con “Fixes”, “Fixed”, “Fix”, “Closes”, “Closed”, or “Close” seguido del #issue cuanmdo el commit se mezcla en la rama master?
* Se cierran los issues  [Cerrando issues via commits](https://help.github.com/articles/closing-issues-via-commit-messages/)
