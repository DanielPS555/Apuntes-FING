
Ipv6 es una tecnologia que no es nueva, pero se esta expaniendo en todo el mundo. 

## Porque hay que pasar a ipv6
- Nos quedamos corto de dirreciones. 
- El cabezal tiene muchas cosas "sucias" que se podian mejorar
- Por algunas cosas de ipv4, teniamos perdida de rendimiento en los routers. 
### Algunas cosas sucicas del cabezal
- Tener un header length debido al tamaño variable del header
- Tener un checksum, el cual hay que recalcular en cada router, ya que cambia el TLL. Eso es una perdida de rendimiento
- La fragmentacion baja el rendimiento, por lo que seria bueno que no fragmente mas. 


## Cabezal Ipv6

![[Pasted image 20221025160006.png]]

- Tenemos dirreciones 4 veces mas grandes 
- No tenemos checksum, todos los datos de los fragmentos, flags, y opciones. 
- Tambien se tiene una *class* que no es mas que un *traffic class*: Describe los diferentes tipos de trafico, al igual que en Ipv4. No esta muy bien definido. Osea sea paso del nombre *TOS => Traffic class*.
- Se agrego el *identificador de flujo*, este identificador se crea para identificar los paquetes que coreesponden a un mismo flujo, por ejemplo una llamada o una trasmicion. Pero la realidad es que ni los desarroladores de ipv6 definieon exactamente que es un flujo. 
  Un flujo queda identificado por la ip de origem, ip de destino, y el numero de flujo. Le indica a los routers que esos paquetes tiene que ser tratados de forma simular, o tambien se puede utilizar para reservar recursos. No sabemos como, pero el router podria tratarlo de forma particular. 
- Cambiaon el *TTL* por "*hop count*"
- *Payload length* : es el tamaño del contenido, osea no se cuenta la cabecera de IPv6 que tiene 40 bytes. AHora el payload maximo es 65536  bytes.
- *Next header* : puede tener dos propocitos, puede indicar una *extension-header*, lo que haria de remplazo al apartado de opciones del Ipv4. Pero su uso mas comun es identificar al protoclo de la capa superior al que se le debe entregar el payload. Esto implica un cambio de semantica. 
- Ahora tenemos un largo fijo del header de 40 bytes

### Extension header 
Ya que quitamos el campo de opciones de cabezal, los *extension headers*  vendran a hacer ese trabajo. Los extension heades le indican el siguiente cabezal a leer, este puede ser TCP o UDP (se mantiene los mismos numeros que en Ipv4 (TCP = 6, UDP = )). Pero puedo tener nuevos numeros. De esta forma, luego de la dirrecion de destino, se añaden segmentos que son las extenciones, que  como primera informacion tiene el next header de la siguiente extencion o de la carga util que va dentro del paquete en si. 
![[Pasted image 20221025162226.png]]

Algunos de los codigos de extension headers pueden ser los siguientes: 
- Hop by Hop header (NH = 0) : Si esta presente, indica que tiene que hacer cada router con este paquete (rompe la regla de procesamiento de tiempo constante por router)
- Routing header (NH = 43)
- Fragment header (NH=44)
- Authentication header (NH= 51)
- Encapsulated securrity payload (50)
- Destination option(NH=60): Si esta presente le indica al destino algo para hacer. 

Notar que hay dos headers muy interesantes. El *Fragment header* y el *Routing header*.

#### Routing header 
En el cabezal de routing, tra una lista de dirreciones ipv6 que le dice a los routers la routa que debe recorrer los paquetes. En Ipv4 los routers son los unicos que resolvian esto. Esto sirve para espesificar el camino, pero puede no enviarlo si quiere  

**Importante**: Si me llego un datagrama con un Routing header, **NUNCA** puedo devolver un datagrama con el routing header inverso, a menos que haya un  Authentication header.

#### Fragment header 
Ipv6 **NO** permite que los routers fragmenten los datagrama como si hacia Ipv4. Si permitimos la fragmentacion en Ipv6 pero solo en las puntas de la comunicacion, osea emisor y receptor. 
La idea que es el emisor envia algunos datagrama, buscando que fallen y por ICMP los routers le informen de su MTU. De esta forma buscamos el *path MTU* . Luego dividimos el datagrama en fragmentos de esta MTU y añadimos un header llamado *fragment header*
La forma es la siguiente:
![[Pasted image 20221025163706.png]]
**Importante:** 
- El fragment offset trabaja en unidades de octetos, e indica el nº de octeto donde comienza el fragmento medido en el paquete original. 
  Osea este framento inicio el en byte (fragment offset)* 8. 
- La flag *M* es 0 si este es el ultimo fragmento, 1 sino. 
- Solo podemos la informacion que se encuentra luego del *frament header* lo que esta antes NO se puede fragmentar. 
- El valor minimo para el MTU es 1280 bytes (eso es exigido por ipv6), osea si fragmentas a 1280 100% que va a funcionar. 
El RFC define una sugerencia para el orden de los extencion headers. 

## Tipos de dirreciones de Ipv6
Tenemos 128 bits para las dirreciones. 

### Tipos de dirreciones Ipv6
#### Unicast 
Identifica exactamente a una interface 
Dentro de esta categoria podemos distingir algunos casos: 
- *global*: Esta ip identifica a una unica interfaces en el mundo. Todas las Globalunicast tiene que tener el prefijo 2000::/3.
- *link-local*: Esta dirrecion solo tiene sentido dentro de un link. Nunca se puede hacer forward fuera de ese link. Todas las link local unicat tiene que tener el prefijo FE80::/10
- *Unique local*: Esto se utiliza para las dirreciones privadas dentro de una red privada. Todas las unique local unicast tiene que tener le prefijo FC00::/7. Se reserva para counicaciones locales dentro de un site. No es ruteable por internet, pero si puede serlo dentro de un sito. 
- *Ipv4 mapped*: Se utiliza para mappear con ipv4. 

##### Formato de la dirrecion de un *global unicast*
![[Pasted image 20221025174118.png]]
El *global routing prefix* es el designado por el RIR (registradora de internet regional) y el ISP al sitio. Luego el *Sub-net id* es utilizado por los administradores para identificar una red espesifica dentro del side proveeido por el proveedor. Por ultimo la parte de la interface identifica a cada equipo, por lo general se utiliza el algoritmo **EUI-64** que permite por medio de la MAC, crear un identificador de 64 bits unico. 
![[Pasted image 20221025175001.png]]
Aunque esto tiene un defecto de seguridad, identificas perfectamente a la maquina. 

##### Formato de dirrecion de un *unique local*
Aqui notemos que ISP independiente pueden utilziar este formato en sitios con o sin acceso a internet. 
![[Pasted image 20221025175450.png]]

#### Mutlicast
Identifica a un grupo de interfaces. Un paquete enviado a una dirrecion multicast es entregado a cada miembro del grupo. Todas ellas tiene un prefijo de FF00::/8.  Un caso particular es el broadcast en el que estan todas las maquinas.  

#### Anycast
Identifica nueamente a un grupo, pero un paquete enviado con esta dirrecion, solamente le es enviado al miembro "max proximo" del grupo. Eso es muy util cuando quiero obtener algo de alguno de los servidores que dan un servicio, y solo me interesa la respuesta del max proximo. 

### Algunas coas mas
- Tambien existe el concepto de subred en ipv6. 
- El *loopback* de ipv6 es ::1/128 o ""::1"
- La *unspecified address* es la 0:0:0:0:0:0:0:0, o se puede escribir como "::" o "::/128".-
- La *Default route* que se usa en las tablas de routeo, es "::/0"

### Alguna notacion
- Se puede abrevar los 0 al inicio de cada grupo. 
- Solo se puede compactar un conjunto de ceros
- Los grupos que son todo 0 se puede abreviar por "::"
- Esta lo que se llama *Ipv4 compatible*, que era escribir la dirreccion ipv4 pero con 96 cero delante y de escribica como ::164.73.32.2. **Esta deprecada**
- Se propuso el *Ipv4 mapped* que es una mejora del Ipv4 compatible. Esto conste en agregar 16 bit con uno delante de la dirrecion ipv4. Y todo lo previo en 0, por lo que queda en ::FFFF:164.73.32.2. 

##  Dirreciones Ipv6 obligatorias 

### Dirreciones obligatorias para todo host
Todo host tiene que tenes una serie de dirreciones configuradas.
- Una dirrecion link-local para cada interface 
- Todas las dirreciones unicast o anycast manual o automaticamente configuradas
- Dirreciones multicast para todos los gupos a los que perteneza el nodo
- El *loopback* address
- Direccion de multicast *AllNode* (esto es un remplazo al broadcast) para FF01::1 y FF02::1
- Dirrecion multicast *Solicited-node* para cada unicast y anycast 

### Dirreciones obligatorias para todo router
- Todas las dirreciones de un host [¿Que seria esto?]
- Dirrecion anycast *Subnet-router* para todas las interfaces utilizadas para hacer forwarding de paquetes
- Todas las dirreciones anycast configuradas
- Una dirrecion de red multicast llamada *All-router* para FF01::2 y FF02::2.


## ICMP Ipv6
- Es obligatorio en la suit de protoclos, y debe estar completamente inplementado en todos los nodos. Eso en Ipv4 no era obligatorio. Por lo que no se puede no contestar un ping por ejemplo. 
- Utiliza el NextHeader = 58
- Se utiliza para reporta errores y realizar pruebas. 

### Icmp mensajes 


[Falta hablar de eso, mirar diapositiva ]



-------------

## Notas de la clase 
- La idea era cambiar de a poco el stack de protoclo, sin afectar la capa de transporte ni la capa de enlase. 
- La idea era convinar el paquete Ipv4 (que tiene por ejemplo dentro ICMP, IGMP, ARP) en un solo que seria Ipv6. 
- *Link MTU* Maximun trasmission Unit, osea lo maximo que puede tranferir de una la capa 2
- *Path MTU*: es el mimo de todos los Link MTU de un camino

