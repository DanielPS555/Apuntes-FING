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
- Ofrece una mejor comparticion de las capacidades de trasmicion exisentes
- Como los conmutadores trabajan a demanda, en los tiempos de inactividad no se desperdician recursos, mientas que en la conmutacion de circuitos si lo hace. 