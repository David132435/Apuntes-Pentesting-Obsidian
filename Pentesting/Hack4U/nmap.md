----
- tags: #reconocimiento
-----
### Ver parámetros para firewalls o IDS (Intrussion Detection System)
nmap --help (Buscar apartado de Firewalls)


### Fragmentar los paquetes del escaneo para eludir un firewall
nmap -f 10.10.10.2


### Buscar scripts
locate .nse


### Listar las categorías de los scripts
locate .nse | xargs grep "categories" | grep -oP '".*?"' | sort -u


### Lanzar todos los scripts que pertenezcan a la categoría "vuln" y a la categoría "safe" (tiene que pertenecer a ambas)
nmap -p22 10.10.10.2 --script="vuln and safe"
(***Es mejor especificar los puertos***)



### Lanzar todos los scripts que pertenezcan a la categoría "vuln" o a la categoría "safe" (Puede no pertenecer a ambas)
nmap -p22 10.10.10.2 --script="vuln or safe"
(***Es mejor especificar los puertos***)


### Descubirmiento de hosts en una red (Más en [[Descubrimiento de HOSTS en una red]])
nmap -sn 192.168.1.0/24 
