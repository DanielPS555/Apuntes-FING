# Procesamiento en cadena en un protoclo de tranferencia de datos fiable

Se define la *tasa de utilizacion del emisor* al tiempo en el que el emisor esta realmente ocupado enviando bits al canal. En caso que el delay de propagacion sea muy elevado, entonces la tasa de utilizacion del emisor sera muy baja. 
Es por eso que se usa lo que se conoce como *piplining* o *procesamiento en cadena*, lo cual consiste en enviar multiples paquetes sin esperar la confirmacion de los mismos. 

Con el fin de utilizar esa tecnica, se debe como minimo 
- Aumentar el rango de numero de secuencia disponibles para los paquetes.
- El lado emisor y receptor tiene buffers que pueden contener mas de un paquete.

Se presentan dos metodos: *Go back N (GBN)* y *Selective repeat (SR)*


## Go back N (GBN)

Con ese metodo podemos tenes N paquetes sin reconocimiento y en envio. 
Podemos definir a la *base* con el numero de secuencia del paquete mas antigo sin reconocer, y a *signumsec* al numero de secuencia mas pequeño aun no utilizado. 

Aqui podemos definir 4 rangos
- [ 0 ,  base - 1] corresponde a los mensajes ya reconocidos
- [base , signumsec - 1] corresponde a los mensajes enviados pero aun no reconocidos
- [signumsec , base + N - 1] son los numero de secuencia aun no utilizados por ningun paquete pero en caso de ser usados se enviaran automaticamente 
- [base + N , ....] son los numero de secuencia que aun no puede ser utilizados. 

A N se lo conoce como *tamaño de ventana*. Y tambien se dice que GNB es un *protocolo de ventana deslizante*.

El receptor de GNB espera por un paquete con un numero de secuencia determinada, en caso de llegar un numero de menor secuencia distinto al esperado, se devolvera un ASK con el anterior numero de secuencia reconocido (uno menor al esperado). Si se recive el esperado se devuelve un ASK con ese numero de secuencia y se aumenta en 1 el numero de secuencia esperado. Por lo tanto si tenemos que el receptor espera un numero de secuencia t, entonces todos los paquetes con un numero de secuencia menor ya habran sido reconocidos por el receptor, a esto ultimo se lo llamada *reconocimiento acumulativo.*

Notar que el receptor tiene como base a un numero mayor al ultimo reconocimiento que haya resivido, osea que si se perdieron ASK y luego recivo otro ASK con un numero de secuencia mayor a los perdidos, asumo que esos paquetes le llegaron al receptor. 

El temporizador solo se reinicia una vez que se vuelve a enviar el paquete base, cuando el temporizador se vence, todos los paquetes de la ventana son re-enviados en simultanio. 

![[Pasted image 20221005153447.png]]

![[Pasted image 20221005153925.png]]



## Selective repeat (SR)
Con un tamaño de ventana grande, y tenemos un *ancho de banda-retardo* elevado, si el primero de los paquetes falla (o uno de los primeros), todos los paquetes que estaben en el canal fallaran, forzando a retrasmitirlo de forma completamente inecesaria, ya que estos en realidad estaban bien, solo fallo en primero. 

El metodo de repeticion selectiva evita esee problema, ya que se tiene que confirmar cada paquete de forma indivitual. Al igual que el emisor, el recetor tiene une ventana, dicha ventana acepta que le llege cualquier paquete, confirmado el mismo. A medida que los paquetes van llegado al receptor, el mismo ira moviendo su ventana hasta estar frente al primer hueco que encuentre (osea lo mueve si el que llego coresponde a la base de la ventana). Analogo para el emisor con los paquetes de reconocimiento. En el caso del receptor, a medida que la ventana se va moviendo, los paquetes cuyo numero de secuencia dejaron de esta en la ventana suben al socket correspondiente. Los paquetes que llegaron al receptor pero faltan paquetes previos (hay un hueco) son retenidos en uno de los buffers del receptor. 

El emisor tiene un timer indivitual por cada paquete que envio de la ventana, cuando vence vuelve a enviar ese paquete nuevamente. 

**Cosas importante:** 
- Cualquier paquete que llege corrputo al receptor va a ser ignorado. 
- Si un paquete llego correctamente  y esta *dentro de la ventana*: se carga dentro del buffer del receptor, se avanza la ventana si se puede y se devuelve el ASK para ese numero de secuencia.
- Si un paquete llego correctamente, pero su numero de secuencia esta entre [base_receptor - N, base_receptor - 1] se debe devolver un ASK con el numero de secuencia de *ese* paquete. Osea de un paquete atrasado, eso se hace porque si el ASK del receptor al emisor se piede, y cuando el emisor vuelve a enviar el paquete al receptor no le envia su numero de secuencia, entonces la ventana del emisor queda trancada. 

![[Pasted image 20221005161436.png]]





**Importante en general**
Tanto en GNB como en SR, es importante que para no entrar en estado incoherentes el tamaño de la ventana sea menor a la mitad del rango numerico de numero de secuencia. Sino un numero de secuencia pasado se podria confundir con uno de la ventana actual. 



