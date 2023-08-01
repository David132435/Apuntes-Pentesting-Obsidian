------
- tags: #web #burpsuite 
---------------

## Ideas para bypassear:
### 1. Eliminar la validación desde F12
> Si el código HTML de la página muestra que al hacer submit, se envía una petición por post y se valida que estemos subiendo el archivo correcto, podríamos eliminar la parte HTML que hace que se valide, por lo que ya no se validaría

### 2. Extensiones alternativas
> 	Si se prohíben explícitamente archivos con extensión .php, podemos usar extensiones alternativas que también ejecutarán código php como: 
> 		._php_, _.php2_, _.php3_, ._php4_, ._php5_, ._php6_, ._php7_, .phps, ._phps_, ._pht_, ._phtm, .phtml_, ._pgif_, _.shtml, .htaccess, .phar, .inc, .hphp, .ctp, .module_

(De este modo, en ocasiones, lograremos subir archivos pero no serán interpretados por el servidor, deberemos probar con diferentes extensiones hasta dar con una que funcione)


### 3. Subir un .htaccess y definir una nueva política
> SI podemos subir un .htaccess, podemos decirle al servidor que a partir de ahora nos interprete una determinada extensión como extensión de php y por lo tanto nos ejecute el código.

#### Como hacerlo:
filename: .htaccess
Content-Type: text/plain
Contenido:
AddType application/x-httpd-php .test

De este modo, las extensiones .test serán interpretadas como .php

### 4. Límite por tamaño máximo de archivo
> Si el servidor nos limita por tamaño máximo del archivo de podemos subir, podríamos:
> 1. Modificar dicho límite de tamaño si es que podemos llegar a controlarlo desde nuestro lado (Con [[BurpSuite]] por ejemplo)
> 2. Acortar el payload. Nuestro payload podría ser así:

	<?php system($_GET[0]); ?>

Para mas tarde hacer:

	uploads/payload.php?0=whoami

Se puede acortar aún más así:

	<?=`$_GET[0]`?>


### 5. Cambiar el Content-Type
> SI el servidor valida el campo Content-Type, podemos modificarlo a nuestro gusto, por ejemplo, podríamos poner
> Content-Type: image/jpg en caso de que el servidor admitiese imágenes


### 6. Magick Numbers
> El servidor puede llegar a detectar que intentamos subir un archivo php a través de los magick numbers.
> Para evitarlo, podemos cambiar el Content-Type a image/gif y poner en el inicio del script en php "GIF8;" de este modo 
> el servidor entenderá que es un archivo gif.


### 7. A través de MD5
> Si al subir cmd.php el servidor nos lo guarda como una cadena en MD5 seguido de .gif, podemos computar el hash MD5 de cmd (que es el nombre del archivo) o de cmd.php (habría que probar ambos) o incluso al contenido del archivo que subimos y buscarlo en el directorio /uploads/ seguido de .php


### 8. Doble extensión
> Si el servidor valida que el nombre del archivo contenga 'jpg', pero no necesariamente acabe, podemos subir un archivo llamado:
> cmd.jpg.php y este será aceptado por el servidor




















