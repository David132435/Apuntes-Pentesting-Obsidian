---------
- tags: #burpsuite #web #lfi #web #system #rce
---------
Para ver como explotar in LFI, mirar [[LFI]]


### Interesting Files

/etc/passwd
/home/user/.ssh/id_rsa
/proc/self/environ
.htpasswd
<Código fuente de si es una web en python/javascript>



### Log poisoning

##### Apache
/var/log/apache2/access.log

##### SSH
/var/log/auth.log
/var/log/btmp