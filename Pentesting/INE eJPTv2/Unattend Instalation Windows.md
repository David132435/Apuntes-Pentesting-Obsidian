-------------------
- tags #windows 
--------------
> Si se tienen que configurar varios equipos en una red (10, 20, 50 equipos...) se puede utilizar la herramienta "__Unattend Windows Setup__" para 
> configurarlos todos a la vez. Sin embargo, esto puede dejar rastro en un fichero __unattend.xml__, donde se pueden
> llegar a quedar credenciales de usuarios creados. La ruta es la siguiente:

	C:\Windows\Panther\unattend.xml


En el ejemplo de la imagen, el valor de PlainText es false, lo que significa que la contraseña esta en base64 y no en texto plano.
![[Pasted image 20230731162735.png]]