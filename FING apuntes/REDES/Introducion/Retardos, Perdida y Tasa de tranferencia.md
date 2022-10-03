# Retardo, Perdida y Tasa de tranferencia de paquetes
Cuando un paquete viaja de un nodo a otro a lo largo de una ruta, sufre retrasos. Los retrasos mas significativos son:
- `Retraso de procesamiento nodal`: Es el tiempo que le lleva al router procesar el paquete. Esto puede ser porque esta chequeado errores o porque esta analizando cual es el siguiente router a enviar.
- `Retraso de cola`:  Es el tiempo que en el que el paquete espera en la cola para ser enviado.
- `Retraso de trasmision` : Es el tiempo necesario para colocar todos los bits del paquete en el enlase. Si $L$ es el tamaño del paquete (media en bits) y $R$ es es la velocidad de trasmicion (medica en bit/seg). Entonces el retardo de trasmicion sea $L/R$ seg.
- `Retraso de propagacion`: Es el tiempo que le lleva al ultimo bit del paquete llegar al otro nodo una vez que es colocado en el enlase: Si $D$ es la longitud del enlase (media en metros) y $S$ es es la velocidad de propagacion del material (medica en metros/seg). Entonces el retardo de propagacion sea $D/S$ seg.

## Algunas cosas a tener en cuenta
- Cuando un paquete llega completamente al router, puede ser trasmitido inmediatamente o puede ponerse en la cola. En caso que se este enviando otro paquete o haya otros elementos en la cola, el paquete recien llegado ira a la cola.
- El retraso de propagacion no le importa el tamaño del paquete, ya que es la velocidad  a la que los bits viajan en el enlase. Por otro lado en el retraso de trasmicion no importa la distancia a recorrer, solo que tan rapido el enlase acepta los bits y cuandos de estos debo colocar en el enlase.
- Se llama retraso nodal a la suma de los 4 retrasos en cada nodo
	$d_{nodal} = d_{proc} + d_{cola} + d_{trans} + d_{prop}$

## Retardo de cola y perdida de paquetes
El retardo de cola es variable segun los paquetes que van llegando y que estaban actualmente en la cola. Es por eso que para medirlo se utilizan otras medidas.
Con el fin de analizar de mejor manera el retardo de cola, se define a continuacion la *intensidad de trafico:* 
	**Def (Intensidad de trafico)**
	Sea `a = velocidad media en que llegan los paquetes` , `L = tamaño de los paquetes` y `R = la velocidad de trasmicion`
	Entonces la intencidad de trafico es $I=\frac{La}{R}$
	
Notar que si $I > 0$ entonces llegan en promedio mas paquetes que los que en nodo puede sacar, por lo que la cola creese hasta el infinito, y por ende tambien el $d_{cola}$. 
Como la llegada de paquetes es aletoria, no es 100% confiable esta medida. Lo que si se puede observar es que a medida que $I$ se aproxima a 1, el $d_{cola}$ crese exponencialmente, mas, tiende al infinito. Este efecto es similar al de una autopista cuando hay un trancaso (hay $I$
es simular a 1)
![[Pasted image 20221002184635.png]]

El retraso por cola esta acotado a un cierto tiempo ya que la cola tiene un tamaño finito. Una vez que la cola se desborda se comienzan a perder paquetes. Es por eso que *El rendimiento del nodo tambien se mide en perdida de paquetes*, no solo en el retraso de cola.

## Retardo extremo a extremo

En caso de tener N nodos, con el mismo retraso en propagacion, trasmicion y procesamiento, y 0 retraso en cola. Obtenemos que el retraso extremo a extremo es el siguiente: 
$d_{extremo-extremo} = N+1(d_{proc} + d_{trans} + d_{prop})$

## Tasa de transferencia
La *tasa de tranferencia instantania* es la velocidad a la que el host receptor recive el archivo, expresada en bits/seg. 
La *tasa de tranferencia media* es $F/T$ donde $F$ es el tamaño del archivo y $T$ es el tiempo total que el que se llevo la transferencia. 
El *enlase cuello de botela* es el `enlase de menor velocidad de trasmicion que se tiene a lo largo de la ruta`. Esta es la maxima velocidad que se podria obtener. Es por eso que generalmente la limitante en las tranferencia es la red de acceso, ya que el nucelo de la red trabaja con velocidad de trasmicion muy elevadas.

De todas formas la tasa de tranferencia no esta unicamente determinada por la velocidad de trasmicion del enlase cuello de botella, tambien esa afectada por el trafico existente, por ejemplo si se tiene que multiplexar un enlase, ya perdemos velocidad en el mismo, por lo que nuevamente perdemos tasa de tranferencia.