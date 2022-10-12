# Mecanismo de control de congestion TCP

Otros de los componentes claves de TCP es tu *mecanismo de control de congestion*. El cual utiliza un *control de congestion terminal a terminal* y no el de control de congestion asistido por la red.

TCP limita la velocidad a la que emite dependiendo de la congestion. Si la congestion es baja o nula aumenta la velocidad y si se presenta en mayor medida, la velocidad disminuye. 

## Como limta su velocidad en base a la congestion

TCP define otra variable de conexion llamada *ventana de congestion (VentCongestion)* que acota la velocidad de tranferencia en funcion de ella. Sigiendo la siguiente formula

$UltimoByteEnviado - UltimoByteReconocido \leq min\{VentCongestion, VentRecepcion\}$ 

Por lo que si se recalcula la ventana de congestion cada *RTT* segundos, y si ademas despreciamos la Ventana de Recepcion, tendremos que el emisor es capaz de emitir como max VentCongestion bytes cada RTT segundos.

## Como se percibe la congestion el emisor TCP
Se define un *suceso de perdida* cuando el temporizador vence o cuando se reciven 3 ASK duplicados. Entonces ante un suceso de estos, el emisor entiende que hay congestion (y desminuye la ventana de congestion), por otro lado, si se van reciviendo ASK que confirman segmentos enviados, esa ventana aumenta. Mientras mas rapido se recivan estas confrimaciones, mas rapido se aumenta la ventana. 

Como TCP utiliza los paquetes de confirmacion para incrementar su ventana de congestion, se dice que TCP es *auto-temporizado*. 

## Determinar la ventana de congestion
Primero que nada cuando se reciven ASK de nuevos segmentos, la velocidad *debe aumentar* y cuando se da un *suceso de perdisa* se *debe disminuir* la ventana. 
Ya que un suceso de perdida (un segmento perdido) implica **Congestion**.
Luego de debe tantear la ventana en base a lo antes dicho. Osea ir aumentando la velocidad cuando se puede hasta que se da un suceso de perdida y se debe retroseder. 

El algoritmo de control de congestion TCP tiene 3 grandes componentes:
1. *Arranque lento*
2. *Evitacion de la congestion*
3. *Recuperacion rapida*

Vamos a resumir cada uno de estos a continuacion

### Aranque lento
Este es el estado inicial. *VentCongestion* inicia en 1 MSS. Y luego por cada ASK nuevo (que reconosca algo no reconocido hasta el momento), se aumenta en 1 un MSS mas. Por lo tanto por cada RTT, la VentCongestion se duplica. La idea de este estado es que rapidamente se pueda alncasar una velocidad aceptable.

### Evitacion de congestion
En este estado, estamos proximos a una posible colicion, por lo tanto aumentamos un MSS por RTT, no duplicamos como si se hacen en el araque lento. Por *defecto UmbalAL* = 64KB.

### Recuperacion rapida
EN este estado estamos intentando solucionar un hueco que se geneado por la llegada de un paquete fuera de orden. Por lo tanto a media que llegan mas duplicados, aumentamos la ventana de congestion hasta recivir un ASk nuevo (lo que indica que el hueco se soluciono), y volvemos al estado de ecitacion de la congestion. 

Se omite el detalle de cada uno ya que esta todo explicado muy bien en esta maquina de estados: 

![[Pasted image 20221008175005.png]]

Si ingoramos el aranque lento, este algoritmo se comporta de la forma *crecimietno aditivo y descrecimiento multiplicativo (AIMD)* , en otra palabras crece de a uno por RTT (incremental) y decrece multiplicativamente (divicion entre dos)

### Variantes TCP
*TCP Tahoe* es una version previa al *TCP Reno*, una de sus diferencia es que TCP Tahoe reinicia el VentCongestion ante cualquier susceso de perdida, por lo que no tiene recuperacion rapida. TCP Reno si la tiene. Luego *TCP Vegas* analiza los RTT de los paquetes que llegaron para prededir una congestion inminente (SI el RTT ha aumentado considerablemente es una señal de proxima congestion) y modificar su velocidad considerando esto ultimo. 

## Tasa media de tranferencia de una conexcion

Hay dos formulas para podr estimar eso: 

1. Sea W = valor cuando la ventCogestion detecta una perdida. Donde RTT y W son constantes, se omite o ignora la etapa de aranque lento. se consigue:
$\text{tasa tranferencia media} = \frac{0,75.W}{RTT}$ 
2. Sea L = tasa de perdida. Si L, MSS y RTT son constantes entonces:
$\text{tasa tranferencia media} = \frac{1,22.MSS}{RTT.\sqrt{L}}$ 


## Equidad
- Si en un enlase cuello de botella tenemos una velocidad de trasmicion de R bit/seg y tenemos K conexciones TCP. Entonces si el MSS y el RTT es el mismo, tienen cada una de estas conexciones a tener una velocida de tranferencia de R/K.
- En la practica aquellas conexciones que tiene un RTT mas bajo consigue apropiarse mas rapido del ancho de banda que las que tiene un RTT mas alto. 
- No puede haber equidad incluso aunque el RTT sea el mismo y no haya conexciones UDP ya que algunas aplicaciones (por ejemplo los navegadores) utilizan conexciones TCP en paralelo, lo que aumenta su ancho de banda por el numero de conexciones TCP que esta utilizando.
- UDP no tiene control de congestion, lo que hace que envia sus segmentos sin importar el estado de la red. Como TCP si tiene ese control, UDP proboca que TCP tenga que disminutir su tasa de tranferencia por lo que UDP podria exlusar las tranferencias TCP de la red. Muchas aplicaciones de tipo real utilizan UDP por su falta de equidad, lo que le da en sierto punto priodiad en la red.

## Notificacion explicita de congestion (ECN) 
Actualmente algunas redes permiten brindar notificacion explisita a TCP de la congestion de la red. En otras palabras no solamente se utiliza el *control de congestion terminal a terminal* sino que tambien se puede utiliza el *control de congestion asistido por red*. 
Para ello se la *notificacion explicita de congestion (ECN)* . La forma en la que funciona es la siguiente: 
El emisor configura los dos *Bit ECN de la cabecera IP* para indicarle a los routers que tolera ECN el emisor, si se detecta alguna congestion (a criterio del router) ese ultimo modifica estos dos bit indicando que hay congestion (pone ambos bit en 1). Cuando llega al receptor, el mismo lee estos dos bit de la cabecera IP, si un router notifico congestion, el receptor cuando le envie el ASK al emisor, activara la flag *ECE*, la cual al ser recivida por el receptor, *actuara reduciendo el tamaño de la ventana de congestion a la mitad* y el siguiente segmento que le envie al receptor sera con la flag *CWR* activada.  




