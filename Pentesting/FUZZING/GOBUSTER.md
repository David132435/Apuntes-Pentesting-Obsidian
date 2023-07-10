### Búsqueda de directorios/archivos
	gobuster dir -u http://direccion.com/ -w /usr/share/wordlists/SecLists/Discovery/Web-Content/directory-list-2.3-medium.txt -t 200
**Se puede evitar códigos de estado de la siguiente manera -b 403,404
También se puede usar la opción --add-slash
Se puede buscar por extensiones de la siguiente manera: -x php,html,txt (no compatible con --add-slash)
Se puede buscar solo por codigos 200 de la siguiente manera -s 200 -b ''**






### Enumeración de subdominios
	gobuster vhost -w /usr/share/wordlists/SecLists/Discovery/DNS/subdomains-top1million-5000.txt -u http://dominio.com -t 20

**Si el comando te muestra todos los resultados podemos añadir al final "| grep -v 403" suponiendo que nos esté mostrando subdominios que devuelven un código 403**


