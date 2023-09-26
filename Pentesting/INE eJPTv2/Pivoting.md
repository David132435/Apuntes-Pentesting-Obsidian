--------
- tags: #metasploit #meterpreter #pivoting 
-------

### Desde una sesión Meterpreter

	run autoroute -s x.x.x.x/xx

##### Como continuar:
	use auxiliary/scanner/portscan/tcp
	set RHOSTS x.x.x.x
	set PORTS 1-100
	run

	portfwd add -l 1234 -p 80 -r x.x.x.x

> -l Es el puerto que usaremos nosotros para alcanzar el puerto del otro equipo
> -p Es el puerto abierto real en el otro equipo
> -r IP del equipo final al que estamos intentado llegar



















