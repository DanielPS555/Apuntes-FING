# Estructura del segmento TCP

Una vez que el mensaje llega de la capa de aplicacion, *el mismo se divide en fragmentos del mismo tamaño que define el MSS* , cada uno de los mismos se coloca en un segmento TCP.

Cada segmento TCP tiene una estructura que pasaremos a definir a continuacion. 

- *Numero de puerto origen*  : 16 bits
- *Numero de puerto destino*  : 16 bits
- *Numero de secuencia* : 32 bits. Es el numero que utiliza el emisor para decir cual es numero secuencia del 1º byte del segmento. Se profundiza mas adelante.
- *Numero de reconocimiento*: 32 bits. Es el numero de secuencia del 1º byte  que espera el emisor del receptor. 
- *Longitud de cabecera* 4bits. Indica el tamaño de la cabecera TCP expresada en palabras de 32 bits. Osea si el valor de este campo es 5, entonces la cabecera tiene unos 5 * 4 = 20 bytes (o 160 bits)
- *Campo indicadores* : Se cuentan con los siguientes indicadores 
	- ACK: El valor en el campo numero de reconocimiento es valido
	- RST: Se mando una peticion de inicio de conexcion a un puerto para el cual no hay socket
	- SYN: Se utiliza en los dos primeros segmentos de una conexcion, se utiliza con el fin de establecer la conexcion
	- FIN: Se utiliza con el fin de terminar la conexcion. 
	- PSH: Indica que los datos debe ser enviado a la capa superior a penas se resivan
	- URG: indica que hay datos urgentes. 
	- CWR: Usado para control de congestion
	- ECE: Usado para control de congestion
- *Ventana de recepcion* :16bits. se utiliza para el *control de flujo* (como obviamente el lector puede deducir no digo nada de eso porque aun no lei el teorico de esa parte )
- *Suma de comprobacion de internet*
- *Puntero a los datos urgentes*: Apunta al final de la parte urgente del mensaje.
- *Campo opciones*: Es un campo de tamaño variable. Se usa por ejemplo cuando el emisor y el receptor negocian el tamaño del MSS, y tiene otras aplicaciones. Por lo general no se envia nada en el. 
- *Datos* : Aqui viaja el segmento. 


![[Pasted image 20221005194703.png]]


**Importante:** 
- El numero de reconocimiento que envia el host A al host B, es el numero de secuencia del primer segmento que espera recibir A de B. 
- TCP tiene *reconocimientos acumulativos*. Osea si envia un numero de reconocimiento, todos los bytes previos fueron reconocidos. Pero a diferencia de GBN, no descarta los segmentos que le llegaron fuera de orden, los guarda en un buffer del receptor hasta que le llegan los segmentos faltantes (los huecos). 
- Se dice que el reconocimiento de datos esta *superpuesto* al segmento de datos enviado, ya que se envian en el mismo segmento los datos y el segmento de reconocimiento. 