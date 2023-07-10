
### Buscar por subdirectorios/ficheros
wfuzz -c --hc=404 -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -t 20 -u \<url\>/FUZZ
**Se puede usar la opción -L para seguir redirecciones**

### Buscar por ciertas extensiones con WFUZZ
wfuzz -c --hc=404 -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -z list,html-php-txt -t 20 -u http://url.com/FUZZ.FUZ2Z 


### Buscar por rangos
wfuzz -c -t 20 -z range,1-20000 -u http://url.com/?product_id=FUZZ


### Buscar por subdominios
wfuzz -c -w /usr/share/wordlists/SecLists/Discovery/DNS/bitquark-subdomains-top100000.txt -u 'http://topology.htb' -H "Host: FUZZ.topology.htb" -t 20 --hh 6767


### GIT FILES

git-dumper http://pilgrimage.htb/.git/ git