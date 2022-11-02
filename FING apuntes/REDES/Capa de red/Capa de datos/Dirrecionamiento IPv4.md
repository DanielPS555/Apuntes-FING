- Las dirreciones *ip* NO estan asociadas a un host o router, estan asociadas a una *interface* que es lo que conecta al conmutador y al enlase. 
- Una parte de la ip estara determinada por la *subred* a la cual la interface esta conectada. 
- En terminos de IP, una red que interconecta las interfaces de host y una interface de router se la llama *subred*. La subred tiene su propia dirrecion, por ejemplo 223.1.1.0/24 donde el 24 es lo denomina*mascara* y es la que define cuandos bit a la isquierda definen la dirrecion de la subred. 
- Una forma grarfica de ver las subredes de una red, es sacar las interfaces de los routers y de los host (no de los switch) y ver cuales "islas" quedan colgando.


 ## Estrategia de asignacion de dirreciones de internet 
 Hoy en dia la estrategia de asignacion de dirreciones de internet se las conoce como *enrutamiento entre dominios sin clase* *(CIDR)*.
 En esta, si una dirrecion tiene la forma a.b.c.d/x, los x bit mas significativos constituyen la parte de la red, por lo general se lo llama *prefijo*.Por lo general las organizaciones tiene un rango de ip con un rango en comun.
 Esto facilita mucho, ya que los routers externos solo tiene que tener en cuenta en su tabla de routeo ese prefixo.
 
 Algunas cosas a tener en cuenta:
 - Luego el resto de los bits $32 - x$ sean utilizado para los dispositivos dentro de la organizacion. 
 - Utilizando estos bits de menor peso podemos utilizar estructura de subredes adicionales. 


Antes del CIDR se utilizaba en *direccionamiento con clases*, donde habia 3 clases A(/8,) B(/16) y C(/24). 

La dirrecion 255.255.255.255de IP difucion, cuando un host envia este mensaje, el mismo es entregado a todos los host de la subred, incluso se podria pasar a subredes vecinas, aunque esto no es muy comun. 


## Asignacion de dirreciones 
Para poder usar una subred dentro de una organizacion, lo primero que tiene que hacer el administrador de la red es contactarse con el ISP, de forma tal que le informe cual es el bloque ip que el mismo le ha asignado. 
Hay otras formas de obtener la dirrecion, ademas de obtener del ISP el bloque de dirreciones. 

Como se le asignan a los ISP sus bloques de dirreciones? (de forma tal que se maximize la *agregacion de direcciones* ) Eso lo hace una agencia llamada *ICANN*. ICANN hace otras cosas, como manejar los DNS raiz. 

### ¿Como obtener una dirrecion de host?
Se puede hacer manual. Osea que el administrador manualmente vaya maquina por maquian (o remoto) y le asigne su configuracion. 
O puede usar *DHCP*, el cual le da la configuracion al dispositivo. Puede ser configutado para que sea una *dirrecion ip temporal*  o fija para ese dispositivo(no cambie). Tambien le puede dar mas informacion cono su DNS, dirrecion gateway, etc. 

Gracias a la capacidad de DHCP para automatizar el proceso de conexcion, se dice que es un protoclo *plug and play*.

Puede haber un servidor DHCP en cada subred, pero por lo general no es el caso. Aqui existe un *agente de retrasmicion DHCP* para esa subred, que conosca el servidor DHCP para la red. 

#### Pasos DHCP
1. `Descubrimiento DHCP`: Cuando el servidor se conecta a una red, envia un *mensaje de descrubimiento DHCP* . En particular un mensaje con el protoclo UDP, al puerto 67 y con la dirrecion de destino Ip de difucion (255.255.255.255) e ip de origen 0.0.0.0. Este mensaje le llega a todos los de la red. Le añade al paquete un id de transaccion 
	**DUDA**: de donde saca este id?
3. `Oferta(s) del servidor DHCP`: Cuando un servidor DHCP recive el mensaje de descrubimiento, el mismo contesta con una oferta (utilizando el mismo id de transacion), y lo envia de nuevo a la dirrecion 255.255.255.255, pero con su ip de origen. Dentro de este mensaje va la IP propuesta, el ID de transaccion, el tiempo de arrendamiento y la mascara de red. El nombre de este mensaje es *mensaje de oferta DHCP*.
4. `Solicitudes DHCP`: El cliente elige una de las oferta que le llegaron de varios servidores, y le envia un *mensaje de solicitud DHCP* al DHCP que haya elegido para confirmar su eleccion. Notemos que la ip de origen del cliente sigue siendo 0.0.0.0.
5. `ACK DHCP`: El servidor DHCP por ultima vez le envia un mensaje broadcast con un *mensaje ACK DHCP* donde se confirman los parametros y apartir de este momento el host quedo configurado. *DHCP tiene mecanismos de renovacion de sus configuraciones una vez que esta por acabarse tu tiempo de arrendamiento*

Hay una **Falta** fundamental con DHCP, si un host cambia de subred, los socket TCP que tuviera abiertos se pierden. 


## Traducion de dirreciones NAT
Con el fin de no tenes que pedirle al ISP una ip para cada dispositivo de nuestra red (entre otros muchos motivos que aun no he leido :) ), se han inventado las *NAT*. 

Una *red privada* es un ambito donde las dirreciones solo tiene significado para los dispositivos de la red. 

Cuando un mensaje quiere salir al mundo exterior, tiene que pasar por un *NAT*, que generalmente es el router. 

### Funcionamiento resumido de NAT
Todos los paquetes que salgan al mundo exterior van a salir con un numero de puerto y con su dirrecion de origen del router NAT, por lo que dispositivo NAT aparenta ser el unico dispositivo de esa red con una dirrecion fija. 
Toda LAN tiene lo que se conoce como *Tabla de traducciones NAT*, que mapea el la dirrecion y puerto WAN con la de la LAN. Cuando un paquete sale por la NAT, si no estaba en la tabla se crea un registro donde en el lado de la WAN vamos a tener la ip de origen del router y un puerto que el router eligue, y de lado de la LAN la dirrecion de origen y el puerto de origen. 
Luego el router envia el paquete al destino pero con su ip y un puerto que eligio. Cuando el destino le conteste, le va a contestar a la NAT con su ip y su puerto, luego con la tabla de traduciones NAT el NAT le envia ese paquete al verdadero origen. 

Hay dos problemas con NAT
1. Utiliza los numeros de puerto para dirrecionar procesos y no host. Eso genera problemas cuando hay servidores dentro de la red domestica que esperan solicitudes a un puerto bien conocido. Por lo que no nos podemos conectar al servidor. Hay algunas soluciones para esto: 
	 - Lo que se puede hacer es *always forwarded*, es como inicializar una entrada del NAT por defecto. 
	 - Otra solucion que es que el servidor directamente le  habla al router dirrectamente para configurar el forwarding. Osea permite añadir y eliminar *port mappings* y conocer la IP publica. Un protoclo que hace esto es el *UPnP* 
	 - Otra opcion es usar un puente, como es el caso de skype. Aqui hay un servidor llamado skype relay en el cual tanto los clientes con ip publica como las privadas (ocultas tras la NAT) se conectan, y luego este servidor hace de puente entre las dos conexciones (osea une las conexciones de cada cliente con el servidor entre si.)
2. Se esta metiendo un router de capa 3 en datos (puerto) de capa 4. 


## ICMP
ICMP se utiliza como mensajes de control. Cada uno de estos mensajes tiene un *type* y un *code*. 

![[Pasted image 20221025151950.png]]

ICMP le informa al emisor del estado de los paquetes, por ejemplo el router le envia un mensaje ICMP al emisor que mato un datagrama porque le quedo grande el MTU (eso para ipv6), o porque el TTL vencio. Tambien generalmente añade el cabezal y parte de la data del datagrama para que el emisor sabe que datagrama causo el error. *Tracerroute* utiliza esto. 



## Redes privadas 

![[Pasted image 20221027032549.png]]ç
