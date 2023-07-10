openssl s_client -connect tinder.com:443

sslscan tinder.com

nmap --script ssl-heartbleed -p 443 127.0.0.1


**HTTPS puede ser vulnerable a heartbleed, lo que significa que se podría llegar a leakear parte de la memoria y llegar a ver procesos, cookies...**