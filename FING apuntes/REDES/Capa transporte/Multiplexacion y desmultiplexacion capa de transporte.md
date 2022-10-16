# Multiplexacion y desmultiplexacion capa de transporte
Se le denomica *Multiplexacion y desmultiplexacion* a la ampliacion del servicio de entrega host a host al servicio de entrega proceso a proceso. 
Este proceso se aplica cuando tenemos que enviar datos a la capa de red, o cuando redirigimos un segmento proveniente de la capa de red a la capa de aplicacion. 

Es de notar que la capa de transporte no entrega los datos al proceso en si, sino a uno de los *sockets* que el mismo posee. 
Cada *socket tiene un identificador* asociado, el formato de este identificador depende en primer lugar si el socket es TCP o UDP.

- *Desmultiplezacion*: Cada uno de los segmentos tiene un conjunto de datos en su cabecera utilizados para este proposito. En base a los mismos (y capaz a algunos de la capa de red), redirige los datos correctamente al socket.
- *Multiplexacion*: Reune fragmento de los datos de multiples socket, para cada uno de estos fragmentos los divide si es necesario, les agrega su cabecera y los empaqueta en segmentos para pasarlos a la capa de red. 

En las cabeceras de la capa de red, tanto los segmentos UDP como los TCP tiene incluido el *numero de puerto de origen* y el *numero de puerto de destino*. Los numero  de puerto son enteros de 16 bits, donde los numero de puerto menores a 1023 se los conoce como *numero de puerto bien conocidos*.

Alguno de estos puertos bien conocidos pueden ser: 
- FTP : 21, 20
- HTTP : 80
- SMTP : 25
- DNS: 53
- HTTPS : 443
- POP3 : 110
- IMAP: 143

## Multiplexacion y desmultiplexacion sin conexcion
Una vez que llege el datagrama al host receptor, pasara a ser un segmento que llegara a la capa de transprote, desde esa capa de lee el *numero de puerto destino* del segmento y se le envia el mensaje al socket UDP con ese numero de puerto. 

**Importante**: Un socket UDP esta completamente definido por la tupla < IP Destino, Nro puerto destino >. 

## Mutiplexacion y desmultiplezacion con conexcion 
Una vez que llege el datagrama al host receptor, pasara a ser un segmento con una cabecera TCP. Ese segmento puede pertenece a una conexcion TCP ya creada, o puede ser un segmento enviado con el fin de crear una nueva conexcion. Si es el ultimo caso, se redirige al socket con el *numero de puerto de destino*. Pero sino puede corresponder a una conexcion ya creada, el numero de socket de dicha conexcion *dentro del host* se encuentra determinada por el numero de Ip de origen, en numero de puerto de origen, y el numero de puerto del destino. 

**Importante**: Un socket TCP esta completamente definido por la tupla < IP origen, Nro puerto  origen, IP Destino, Nro puerto destino >.  Por un mismo host se puede conectar al mismo servicio en paralelo (cambiando su puerto de origen).



