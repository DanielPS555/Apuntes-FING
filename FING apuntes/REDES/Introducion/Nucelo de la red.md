# Nucleo de la red

Ahora se enfocara en los elementos que componen en interior de la red, por donde pasaran los paquetes para llegar los elementos de un host a otro. 

Cuando un paquete sale de un host, este viaja por el nucleo por una serie de *Conmutadores de paquete*, dentro de los cuales son especialmente se encuentran los Switch y los Routers. El conjunto de Conmutadores de paquete que tiene que ir recoriendo un paquete para llegar de un host a otro se llama *path*.

Los enlases usan toda su velocidad de trasmicion para enviar los mensajes. Por lo que si un medio tiene una velocidad de trasmicion de R bits/seg y el paquete tiene L bits. Entonces se requieren $L/R$ seg para enviar el paquete por el enlase. 

La mayoria de los conmutadores de paquetes utilizan la *trasmicion de almacenamiento y reenvio*. Donde se almacenan los paquetes recividos y luego se envian por donde y a quien corresponda. 
**No se puede re-enviar un paquete hasta que se haya recivido por completo**.

Es por esto que tambien se sufre de *retardo de cola*, donde el paquete debe esperar su turno en la cola del conmutador antes de poder ser enviado. En caso que la cola de desborde y sigan llegando paquetes, se dara una *perdida de paquetes*

## ¿Como un router re-envia un paquete? 
Una duda clara es a quien le va a enviar el paquete el router ahora tiene que re-enviar el paquete, por lo general se lo envia a otro router. Pero para determinar a cual utiliza las *tablas de reenvio* las cuales junto a parte de la dirrecion ip de destino del paquete, determinan a cual router vecino hay que enviarle ahora el paquete para que siga su camino al host de destino. 

Se cuentan con *protoclos de enrutamiento* los cuales se utilizan para definir las tablas de reenvio de los routers. 

## Formas de transportar datos a traves de una red
Hay dos metodos fundamentales: 
- `Conmutacion de circuitos:` En este caso se establese una *conexcion de extremo a extremo*, por lo que los recursos necesarios para estableser una comunicacion entre estos dos host son recervados. Donde nos garantizamos una velocidad de trasmicion constante. Por lo que los mensajes de un host a otro no van a tener que esperar. Aqui no hay demoras inesperadas ni perdida de paquetes. 
- `Conmutacion de paquetes:` En este caso no se reserva ningun recurso, por lo que los mensajes enviado utilizan los recursos bajo demanda, por lo que pueden tener esperas o incluso perderse. 

Dentro la conmutacion de circuito, para no ocupar todo el enlase, el mismo se puede multiplexar, hay dos formas. 
- `FDM`  (por frecuencia) : El espetro de frecuencia del enlase es repartido entre las conexciones, por lo que todas pueden tranferir a la vez, pero usando su frecuencia. 
- `TDP`  (Por tiempo): Si tenemos N conexciones, de divide la unidad de tiempo definida (fija) en N periodos, de forma que se emite cada conexcion en su respectivo periodo de tiempo utiliza de forma exlusiva todo es espetro de frecuencia del enlase. 
 
![[Pasted image 20221002044301.png]]


Ambas formas de asignacion tiene su ventajas y desventajas. 

### Ventajas de la conmutacion de circuitos
- Al ya reservar una velocidad en los enlases que componen la ruta, nos permite hacer que este metodo muy util en los sistemas de tiempo real. Como por ejemplo una conversacion telefonica, aunque esto ultimo esta cambiando.  
- La velocidad de trasmision no se ve afectada por cuantos enlases haya en la ruta.

### Ventajas de la conmutacion de paquetes
- Es mas facil de implementar, evita el tiempo elevado de estableser la ruta y reservar los recursos de los conmutadores. 
- Ofrece una mejor comparticion de las capacidades de los conmutadores exisentes
- Como los conmutadores trabajan a demanda, en los tiempos de inactividad no se desperdician recursos, mientas que en la conmutacion de circuitos si lo hace. 

## Estructura de la red
La estructura del nucleo de la red de internet es bastante compleja. 
Todo comienza con los ISP, tanto los que terminan proveen de internet a los host como los que proveen de internet a los demas ISP. Se pueden distingir 3 niveles de ISP.
Los *ISP de nivel 1* son los ISP globales, por arriva de ellos no hay ningun otro ISP, ellos se conectan entre si, formando una red central.
Los *ISP de nivel 2* son los ISP regioales, los cuales se encargan de proveer de internet a una determinada region. Se conectan  (pagandole) a uno o mas ISP de nivel 1, y ademas ellos tambien se conectan con otros ISP regionales. Para enviar un paquete de un ISP regional a otro lo mas posible es que se tenga que pasar por los ISP de nivel 1. 
Los *ISP de nivel 3*, tambien conocidos como ISP de acceso, son aquellos que proveen de internet a una determinada LAN, se conectan a los ISP regionales. 

Hay varios conceptos mas que hay que ver para aproximarnos a la estructura de la red:

*La conexcion entre pares* es cuando dos ISP de un mismo nivel conectan sus redes directamente, sin pasar por un ISP. Generalmente esta conexcion es libre de cargo para ambas partes. 

Los *IXP* (Internet exchange point) son puntos de reunion donde multiples ISP establesen conexciones entre pares. Estos ultimos generalmente se encuentran en el mismo lugar donde la empresa construyo el IXP. 

Los *PoP* (Point of reference) es un grupo de routers de la red de un proveedor dado, la idea es que los ISP clientes arquilen un enlase de alta velocidad (o un espacio) donde puedan alojar uno de sus router y se puedan conectar a uno de los router del proveedor al que pertenece el PoP. 
Es importante decir que un ISP cliente puede recurrir a la *multidomiciliacion* , lo cual significa que se conecte con varios ISP proveedores en vez de uno solo. De forma tal que si uno falla, el ISP proveedor pueda continuar operando. 

Tambien tenemos las *redes de proveedores de contenido* donde una compañia (como Google) tiene una red privada con toda la infraestructura necesaria para conectarse con sus centros de datos en todo el mundo (no pasa por los ISP de nivel 1). Por lo que siempre y cuando este dentro de su propia red, este puede administrarla y utilízala como prefiere sin cargo. También puede establecer conexión de par con ISP regionales o de acceso. De todas formas, para llegar a algunos ISP, si o si tiene que pasar por los ISP de nivel 1, por lo que también tiene conexiones con estos últimos en caso de necesitarlas.

![[Pasted image 20221002150448.png]]