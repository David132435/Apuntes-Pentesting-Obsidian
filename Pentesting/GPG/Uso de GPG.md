
## Crear par de claves con el uid "David" 

gpg --quick-gen-key "David"



## Exportar la clave pública para el uid "David"

gpg --armor --export "David" > pubkey.asc



## Firmar el mensaje "hola que tal"

echo 'hola que tal' | gpg --clear-sign



## Modificar UID de la clave "David"

┌──(root💀davidalonso)-[~/maquinas/HackTheBox/Sandworm]
└─# gpg --edit-key David                     

gpg> adduid
Nombre y apellidos: {{7\*7}}
Dirección de correo electrónico: david@david.com
Comentario: 
Ha seleccionado este ID de usuario:
    "{{7\*7}} <david@david.com>"

¿Cambia (N)ombre, (C)omentario, (D)irección o (V)ale/(S)alir? V



## Darle confianza al nuevo UID y borrar el anterior

gpg> trust

  1 = No lo sé o prefiero no decirlo
  2 = NO tengo confianza
  3 = Confío un poco
  4 = Confío totalmente
  5 = confío absolutamente
  m = volver al menú principal

¿Su decisión? 5
¿De verdad quiere asignar absoluta confianza a esta clave? (s/N) s

gpg> uid 2

[  absoluta ] (1). {{7*7}} <david@david.com>
[  absoluta ] (2)* David

gpg> deluid

¿Borrar realmente este identificador de usuario? (s/N) s

sec  rsa3072/EA8B41F0D171A316
     creado: 2023-06-24  caduca: 2025-06-23  uso: SC  
     confianza: absoluta      validez: absoluta
ssb  rsa3072/47B636B98D1F8C5D
     creado: 2023-06-24  caduca: nunca       uso: E   
[  absoluta ] (1). {{7*7}} <david@david.com>


