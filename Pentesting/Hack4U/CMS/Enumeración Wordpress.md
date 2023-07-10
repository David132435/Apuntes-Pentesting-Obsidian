### Enumeración básica
wpscan --url http://X.X:X.X


### Enumeración de plugins vulnerables
wpscan --url http://X.X.X.X -e vp --api-token="loquesea"
(De esta forma no tiene por que encontrar todos los plugins)

### Ver plugins desde el código fuente
curl -s -X GET http://X.X:X.X | grep "plugins"
(De este modo veremos rutas como la siguiente: \<script src='http://X.X.X.X/wp-content/plugins/wp-file-upload')


### Fuerza bruta para usuarios/contraseñas
	wpscan --url http://x.x.x.x -U user -P /usr/share/wordlists/rockyou.txt


### xmlrpc.php
Si existe el archivo http://x.x.x.x/xmlrpc.php podemos realizar un ataque de fuerza bruta de usuarios y contraseñas, especialmente si ya conocemos el usuario