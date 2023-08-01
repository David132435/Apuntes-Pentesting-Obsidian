-----
- tags: #cifrado #web #burpsuite 
--------
# ¿Qué es?

> El Padding Oracle Attack (Ataque de Oráculo de Relleno) es una fumada. Sucede a partir de la manera en que una determinada web cifra los datos con CBC en bloques.
> Se puede usar la herramienta padbuster

## padbuster

	padbuster [url] [Cadena de ejemplo] [número de bits (Debe ser múltiplo de 8)] [opciones adicionales]

### Ejemplo
	padbuster http://x.x.x.x qwertyuiopasdfghjklzxcvbnm 8 -cookie 'auth=qwertyuiopasdfghjklzxcvbnm'

> Con esto logramos saber que es lo que contiene la cadena (Ej de resultado: user=david)
> 
- La opción cookie junto con la cadena correspondiente hace referencia a la cookie de sesión, que es a su vez la cadena de ejemplo ya que en ella es donde está el cifrado.


Podemos realizar el proceso inverso para que nos genere una cookie cuyo valor sea user=admin

	padbuster http://x.x.x.x qwertyuiopasdfghjklzxcvbnm 8 -cookie 'auth=qwertyuiopasdfghjklzxcvbnm' -plaintext 'user=admin'



## Explotación con Bit Flipper attack

> Si creamos un usuario llamado bdmin, la cookie cuyo valor ya sabemos que es user=bdmin comparada con la de admin no será muy diferente, por lo que podemos usar el modo Bit Flipper de [[BurpSuite]] para cambiar algunos bytes y conseguir una sesión como admin

Procedimiento:
1. Abrir BurpSuite y capturar la petición con la cookie
2. Ir al Intruder y poner el modo de ataque en sniper
3. En la sección de Payloads seleccionaremos 'Bit Flipper'
4. En 'Format of original data' marcamos 'Literal value'
5. Desmarcamos 'URL-encode this characters'
6. Lanzamos el ataque
7. Esperamos (puede hacer falta esperar un rato hasta que nos convirtamos en el usuario admin)






