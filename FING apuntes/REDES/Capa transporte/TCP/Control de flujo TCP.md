# Control de flujo TCP
La aplicacion a la cual el emisor le esta enviando los datos no lee necesariamente los datos apenas le llegaron, por lo tanto los mismos se guardan en el buffer hasta que el momento de leerlos llege. Pero lo que puede pasar es que la aplicacion emisora envie mas rapido de lo que la aplicacion receptora puede leer, y *por lo tanto termine desbordando el buffer del receptor*. 

Con el fin de que eso no suceda TCP tiene un sistema de *control de flujo* el cual es esencia es un servicio de adaptacion de velocidades. Notar que eso **NO** es lo mismo que los mecanismos de *control de congestion*. 

## Como funciona
El emisor mantiene una variable la cual se llama *ventana del receptor* . 
El receptor le trasmite la informacion de la cantidad de espacio disponible en su buffer en ese instante al emisor via el campo *ventana recepcion* del cabecal TCP. 
Para saber esto, el host B tiene que mantener otras dos variables, el *ultimoByteLeido* por la aplicacion y el *ultimoByteRecibido* del emisor. 

$ventanaRecepcion = bufferRecepcion - (ultimoByteRecibido - ultimoByteLeido)$

Por otro lado, el hostA mantiene otras dos variables, *ultimoByteEnviado* y el *ultimoByteConfirmado* . 
Si se puede asegurar que se cumple la siguiente desigualdad, entonoces el host emisor se asegura de no desbordar el host receptor. 

$ultimoByteEnviado - ultimoByteConfirmado \leq ventanaRecepcion$

En caso que el campo de la ventana del receptor venga en 0 y no se este esperando ningun ASK del receptor, el emisor no tiene forma de enterarse cuando el tamaño de la ventana aumenta. 
Es por eso que el emisor queda enviando 1 byte de informacion al receptor en este caso, esperando un ASK que contenga una ventana del receptor mayor a 0. 
**DUDA:** ¿Ese byte de informacion es nuevo? ¿No puede desbordar el buffer este byte?




