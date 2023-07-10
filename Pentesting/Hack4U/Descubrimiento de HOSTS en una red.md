>**TIP: Si tenemos la red 192.168.1.0/24 pero puede haber subredes, podemos escanear la red 192.168.0.0/16 y de esta forma descubriremos esos hosts que se encuentran en las subredes**

>**TIP 2: Cuanto más alto sea el ratio de paquetes mas probabilidades hay de que no se encuentren hosts que si se deberían de encontrar**

## Con NMAP (también en [[nmap]])
nmap -sn 192.168.1.0/24

## Con ARP-SCAN
arp-scan -I eth0 --localnet

## Con MASSCAN
masscan -p21,22,80,139,443,445,3306,8080 -Pn 192.168.1.0/24 --rate=5000