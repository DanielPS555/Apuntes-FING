# Gestion de la conexcion TCP

Aqui vamos a ver los posibles estados que puede tener una conexcion TCP

## Iniciar una conexcion

A este proceso se lo llama *acuerdo de tres faces*

1. El cliente envia un segmento sin datos de aplicacion, pero con la flag SYN = 1 y ademas con un numero de secuencia elegido por el cliente.
2. Luego el servidor le contesta con otro segmento sin datos de aplicacion, con al SYN = 1, con el ASK = 1, con un numero de secuencia elegido a conveniencia de el (como se combate el ataque por indundacion SYN eligiendo bien este numero) y con un numero de reconocimiento uno mayor al numero de secuencia enviado por el cliente.
3. Por ultimo el cliente responde con un ASK validando el numero de secuencia del servidor, en este paquete ya puede enviar informacion util. 


## Cerrar una conexcion
El proceso de cierre de una conexcion TCP lo puede comenzar tanto el servidor como el cliente, en este caso vamos a ver como es cuando se cierra el cliente:
1. El cliente envia un segmento con la flag FIN = 1 al servidor
2. El servidor le contesta al cliente con un ASK
3. El servidor envia un FIN al cliente
4. El cliente envia un ASK al servidor (en ese momento el cliente entra en un estado de espera de 30 seg, con el fin que si el ASK no llega al servidor, podamos re-enviar)

## Estados del cliente

- *CLOSED* : En este estado comienza el servidor
- *SYN_SEND*: Este es el estado del cliente luego de haber enviado el SYN al servidor
- *ESTABLISHED*: Este estado del cliente luego que el cliente recive el SYNASK. Nosotros enviaremos el ASK al servidor
- *FIN_WAIT_1*: Hemos enviado el FIN al servidor
- *FIN_WAIT_2*: Hemos resibido el ASK de el FIN enviado por el cliente
- *TIME_WAIT*: Hemos resibido el FIN del servidor, nosotros enviaremos el ASK de ese fin, esperaremos 30 seg por si hay que reenviar el ASK al servidor por si se perdio.

![[Pasted image 20221006005908.png]]

## Estados del servidor

- *CLOSED*: El socket comienza en este estado
- *LISTEN:* Creo un socket de aceptacion
- *SYN_RCVD*: Me llego un SYN, envio mi SYNASK
- *ESTABLISHED*: Me llego el ASK
- *CLOSE_WAIT*: Me llego el FIN, envio el ASK del FIN del cliente y el FIN del servidor
- *LAST_ASK:* Espero el ASK correspondiente al FIN que le envie al cliente 
 
![[Pasted image 20221006010722.png]]

