### Tratar de listar el contenido con un null session
	smbclient -L X.X.X.X -N
	smbmap -H X.X.X.X 



### Montar directorio de SMB en tu equipo
```bash
mount -t cifs //X.X.X.X/directorio /mnt/mounted
mount -t cifs //X.X.X.X/myshare /mnt/mounted -o username=null,password=null,domain=,rw
```

(apt install cifs-utils) (el contenido de /mnt/mounted será igual que el del directorio compartido por smb y borrar un archivo en /mnt/mounted lo eliminará también en el directorio de SMB)



### Desmontar directorio 
	umount /mnt/mounted