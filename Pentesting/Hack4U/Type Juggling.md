----------------
- tags: #web #burpsuite #authbypass 
-----------------
# ¿Qué es?
> Permite burlar un panel de autenticación cuyas credenciales están hardcodeadeas en el código de la página (ejemplo: en PHP)



## Ejemplos
Habiendo capturado la petición POST de inicio de sesión:

Si se usa la función strcompare()

	user=admin&password[]=


Si se usa == para comparar en PHP ambas contraseñas convirtiendolas antes a MD5, podemos poner una contraseña cuyo valor en MD5 empiece igual














