# Tranferencia de datos fiable TCP
TCP crea un *servicio de tranferencia de datos fiable* sobre el servicio implementado por IP que es de tipo best effort. 

TCP tiene un unico temporizador, el cual se reseta cuando se tiene que hacer un re-envio o se detiene cuando se enviaron todos los segmentos que habia que enviar. 

Hay 3 suscesos importantes que pueden ocurrir:
1. *Se recibieron datos de la aplicacion*: Se crean los segmentos que sean necesarios considerando el MSS. Para cada uno se sea el numero de secuencia como el numero de secuencia del 1º byte que envia. E inicia el temporizador si no hay otro segmento en envio.
2. *Se vencio el temporizador*:  *Base emisor* es una variable de estado de TCP, la cual representa el mayor numero de reconocimiento obtenido (ojo que los numero de secuencia tiene un rango numerico ciclico, me estoy refiriendo con el numero de reconocimiento que representa al byte mas posterior dentro del mensaje enviado). Cuando se vence el timer se vuelve a enviar el segmento cuyo numero de secuencia es uno mayor que *Base emisor*. 
3. *Se recivio un ASK valido*: SI el numero de reconocimiento obtenido es mayor que *Base emisor* se actualiza el mismo con ese valor, y si no hay mas segmentos de reconocimiento se detiene el temporizador. 

![[Pasted image 20221005221158.png]]


Cuando se vence el temporizador, el tiempo del mismo se duplica, sin importar los RTTMuestras obtenidos. Eso ayuda al *control de congestiom*, ya que al aumentar el tiempo del timer, este host participa menos en congestionar la red. 

## Retrasmicion rapida
Este es un mecanismo que TCP utiliza para poder retrasmitir incluso aunque el timer no haya vencido.
Cuando un receptor recive un segmento con un numero de secuencia mas alto de lo esperado, se genera un hueco, osea que falta al menos un segmento. En esos casos el receptor envia un *ASK duplicado* con el numero de reconocimiento un byte previo al hueco generado. 
Si el receptor recive 4 ask para el mismo numero de reconocimiento (osea 3 duplicados) entiende que tiene que hacer una *retrasmicion rapida*, osea se adelanta al timer, envia el 1º segmento sin reconocer y vuelve a reiniciar el timer (estoy en duda con esto ultimo). 

![[Pasted image 20221005221225.png]]

## Parecido con GBN 
Se podria decir que TCP y GBN se parecen en ciertas cosas, pero hay en otras que no:
- GBN cuando vence el timer envia toda la ventana, TCP no 
- GBN no tiene retrasmicion rapida, si ASK retardaos, TCP si 
- GBN no guarda en un buffer el resto de la ventana aunque le haya llegado bien, TCP si. 

En lo que no tiene parecido TCP y SR yo diria que sobre todo es por el reconocimiento acumulativo. 
