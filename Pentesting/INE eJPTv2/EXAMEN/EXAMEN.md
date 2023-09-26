
# Escaneo de la red

root@kali:~/examen# nmap -sn 192.168.100.0/24
Starting Nmap 7.92 ( https://nmap.org ) at 2023-08-10 12:54 IST
Nmap scan report for ip-192-168-100-1.eu-central-1.compute.internal (192.168.100.1)
Host is up (0.0044s latency).
MAC Address: 02:26:6C:D9:19:FC (Unknown)
Nmap scan report for ip-192-168-100-50.eu-central-1.compute.internal (192.168.100.50)
Host is up (0.00029s latency).
MAC Address: 02:B0:48:AD:15:FC (Unknown)
Nmap scan report for ip-192-168-100-51.eu-central-1.compute.internal (192.168.100.51)
Host is up (0.00028s latency).
MAC Address: 02:A1:E4:0B:DD:88 (Unknown)
Nmap scan report for ip-192-168-100-52.eu-central-1.compute.internal (192.168.100.52)
Host is up (0.00028s latency).
MAC Address: 02:91:45:2B:8D:7A (Unknown)
Nmap scan report for ip-192-168-100-55.eu-central-1.compute.internal (192.168.100.55)
Host is up (0.00031s latency).
MAC Address: 02:81:3B:6A:E0:0C (Unknown)
Nmap scan report for ip-192-168-100-63.eu-central-1.compute.internal (192.168.100.63)
Host is up (0.0073s latency).
MAC Address: 02:99:39:44:E8:B8 (Unknown)
Nmap scan report for ip-192-168-100-67.eu-central-1.compute.internal (192.168.100.67)
Host is up (0.0060s latency).
MAC Address: 02:06:E0:35:33:32 (Unknown)
Nmap scan report for ip-192-168-100-5.eu-central-1.compute.internal (192.168.100.5)
Host is up.



root@kali:~/examen# arp-scan --localnet
Interface: eth0, type: EN10MB, MAC: 02:37:97:1e:7e:0a, IPv4: 192.168.100.5
Starting arp-scan 1.9.7 with 256 hosts (https://github.com/royhills/arp-scan)
192.168.100.1   02:26:6c:d9:19:fc       (Unknown: locally administered)                          NULL
192.168.100.50  02:b0:48:ad:15:fc       (Unknown: locally administered)             PWNED   (Wordpress con plugin vuln) - > No DMZ 
192.168.100.51  02:a1:e4:0b:dd:88       (Unknown: locally administered)            PWNED  (Reverse shell desde IIS)  - > No DMZ    NO DB
192.168.100.52  02:91:45:2b:8d:7a       (Unknown: locally administered)                       PWNED (Drupal, MySQL)                - > No DMZ

192.168.100.55  02:81:3b:6a:e0:0c       (Unknown: locally administered)                        WINDOWS         
192.168.100.63  02:99:39:44:e8:b8       (Unknown: locally administered)                        WINDOWS
192.168.100.67  02:06:e0:35:33:32       (Unknown: locally administered)                        solo ssh


