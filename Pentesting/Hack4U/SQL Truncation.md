------------------
- tags: #web #sql 
----------------
# ¿Qué es?
> El SQL Truncation se da acuando en un panel de autenticación te limitan el número de caracteres para un usuario, correo, etc... 
> Si la limitación se hace en el  lado del cliente (desde el código html), el usuario podría eliminar dicho código y de poner en un panel de registro un usuario que ya exista y exceder el número de caracteres, podría llegar a cambiarle la contraseña

## Ejemplo
Usuario ya registrado:
	david

Límite de caracteres: 5

Nuevo usuario: david         a
Contraseña: 1234

> De este modo, la base de datos recortará los espacios y la a del nombre de usuario y le asignará la contraseña 1234, sobrescribiendo así al anterior usuario









