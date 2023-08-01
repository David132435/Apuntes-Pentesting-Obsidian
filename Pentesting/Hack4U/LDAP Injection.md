---------
- tags: #burpsuite #nmap #ldap #authbypass 
-------------
# ¿Qué es?
> Puerto 389


## Reconocimiento

	nmap --script ldap\* -p389 x.x.x.x


## Explotación
Si por ejemplo hay un panel de login que autentica a usuarios de una base de datos ldap, podríamos usar inyecciones LDAP para bypassear dicho login


