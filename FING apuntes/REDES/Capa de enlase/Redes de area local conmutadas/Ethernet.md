Actualmente ethernet es la red mas utilizada para LAN cableadas. Por lejos....

Las razones principales de su exito son: 
1. Se implemento muy prontamente en el mercado
2. Era mas simple que la competencia
3. Siempre fue igua de rapida o superior que la competencia

En un primer momento se utiliaba una topologia de estrella, donde los nodos se conectaban por *concentradores* (hubs). Como el hub solo replica la señal y lo saca por todas las salidas, lo que ocurre es que si llegan dos tramas en dos interfaces diferentes del hub, abra una colicion. 
Mas adelante se mejoro la topologia cambiando los hubs por switchs, los cuales son dispositivos "sin coliciones" y de capa 2.

## Estructura de la trama Ethernet

Se pone a continuacion la forma de una trama ethernet: 
![[Pasted image 20221116015659.png]]

Campos:
- `Campo de datos` (46 a 1500 bytes): El tamaño es como minimo 46 bytes, y como maximo el MTU, el cual en enthernet es 1500 bytes. Notar que como tenemos una cota infima para los datos, si el datagrama en realidad tiene menor tamaño, entonces con los cabezales del protoclo Ip podremos eliminar los datos de relleno. 
- `Dirrecion de destino` (6 bytes): Es la dirrecion MAC del destino. Si es la dirrecion de difucion o la BB-BB-BB-BB-BB-BB el emisor lo debe procesar. 
- `Dirrecion de origen` (6 bytes): Es la dirrecion MAC de origen. No tiene mas vuelta que eso. 
- `Campo de tipo` (2 bytes): Identifica al protoclo de capa de red al que hay que pasarle la trama. Por ejemplo el valor de este campo si es un mensaje IP o ARP es diferente. Por lo que si un mensaje de ARP llega a nuestro host, no sera entregado a ARP. 
- `Comprobacion de redundncia ciclica` (4 Bytes): Es el codigo `R` que se tiene que enviar para que la concatenacion de los datos + `R` sea divisible por la clave `G`. 
- `Preambulo` (8 bytes): Son 7 bytes con la forma 10101010 para que los relojes de los receptores se sincronicen totalmente con la frecuencia con la que se envia la trama. Luego se envia un byte 10101011 indicado los ultimos dos bytes que comienza la trasmicion de verdad. 

**Importante**
- Ethernet es un protocolo sin conexcion, osea no hay una comunicacion previa entre el host emisor y receptor antes de enviarse la informacion. Ademas que no implementa tranferencia de datos fiable. Lo que traslada el error hasta que algun protoclo se encarga de eso, como es TCP.

> Pero, si el uso prevalente de hoy día de Ethernet es una topología en estrella basada en switches,
que utiliza la conmutación de paquetes de almacenamiento y reenvío, ¿existe realmente la necesidad
de un protocolo MAC Ethernet? Como veremos enseguida, un switch coordina sus transmisiones
y nunca reenvía más de una trama a la misma interfaz en un determinado instante. Además, los
switches modernos son full-duplex, por lo que un switch y un nodo pueden enviarse tramas entre sí
simultáneamente sin interferir. En otras palabras, en una red LAN Ethernet basada en switches no se
producen colisiones y, por tanto, no se necesita un protocolo MAC.

*Paa recordar*: El el libro dice que:  protoclo MAC es el que cordina las trasmiciones de las tramas en multiples nodos [Osea un protoclo de acceso mutlple??? ]. Pero tambien lo usan para llamar al protoclo Ethernet. [Dudoso....]
