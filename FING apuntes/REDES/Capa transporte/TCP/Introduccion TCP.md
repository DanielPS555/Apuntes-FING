# Introducion a TCP

TCP es uno de los dos principales protocolos de la capa de transprote.

Se dice que TCP  esta *orientado a conexcion* , porque antes que los dos procesos se puedan enviar mensajes, deben estableser una comunicacion entre ellos. En ese proceso se establesen un monton de variables de estado TCP.

Los elementos intermedios de la red no ejecutan protoclos de la capa de transporte, por lo que la informacion referente a TCP dentro del paquete no se ve alterada por el nucleo de la red.

Las conexciones TCP son *punto a punto*, osea entre dos procesos, TCP NO permite la *multidifucion* (osea de un host a varios host). Ademas las conexciones TCP soporta servicio *full-duplex*

Toda aplicacion TCP tiene un *socket de acceptacion* el cual es contactado por el cliente cuando quiere establecer una conexcion, luego de que se da el proceso de establesimiento, se crea un nuevo socket en el servidor destinado exlusivamente para esa conexcion. Durante ese proceso que se llama *acuerdo de tres fases*, se envian 3 paquetes, el primero y el tercero son del cliente al servidor y el segundo del servidor al cliente. Los dos primeros paquetes no tiene carga util. 

Tambien luego de haber establesido la conexcion, se crean un conjunto  de variables de estado, como por ejemplo un *buffer emisor* y un *buffer receptor*. Cuando un cliente TCP quiere enviar datos por un socket, este socket prepara los datos y los deja en el buffer de emision. 

La maxima cantidad de informacion del mensaje que se puede añadir al segmento esa definida por el *MSS*. A su vez el MSS se elige de forma tal que se garantice que la suma del segmento TCP + las cabeceras TCP/IP *se ajuste a unica trama de la capa de enlase*. Tambien es de mencionar que el MSS esta acotado por el *MTU* (que es el maximo tamaño de la trama en la capa de enlase.) 
**Importante**: el MSS NO es el maximo tamaño del segmento, es la maxima cantidad de informacion del mensaje que se puede introducir dentro del segmento.

Tambien es apropiado para una introducion mencionar que es un protoclo con las dos siguientes cualidades:
- Un mecanismos de *tranferencia de datos fiable*
- Un mecanismos de *control de congestion*
- Un mecanismos de *control de flujo* 







