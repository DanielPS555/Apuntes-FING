Hay dos tipos de enlase 
- `Enlace punto a punto`; Solo un emisor de un extremo del enlase y un unico receptor. Algunos ejemplos de protocolos: Protocolo punto a punto (PPP) y el protocolo de control de enlase de datos de alto nivel (HDLC)
- `Enlase de difucion`: Aqui hay varios emisores y receptores en el mismo y unico canal de *difucion* compartido. Es de *difucion* ya que todo lo que difunde un nodo por la trama, le llega a los demas una copia. Ethernet y las redes LAN inlambricas son ejemplos de eso.

Un problea muy grande se puede cordinar a los emisores y receptores de un mismo canal de difucion compartido. A este problema se lo conoce como *problema de acceso multiple*. 

Las computadoras tiene estos protocolos que regulan las trasmiciones al canal de difucion. 

Cuando dos nodos trasmiten tramas, si las trasmicion es al mismo tiempo, puede pasar se mezclen los bit que los receptores estan reciviendo, cuando esto pasa, las tramas *colicionan*. Puede pasar que todos los receptores obtenen estas tramaas colisionadas. 

Se puede dividir en 3 categorias los protocolos de acceso mutlple:
- `Protocolos de particionamiento del canal`
- `Protocolos de acceso aletorio `
- `Protocolo de toma de turnos`

Ademas es desable que se tengan las siguientes cualidades en un canal de difucion con R bps: 
- Cuando solo un nodo tenga que tramsitir, este tenga una tasa de tranferencia de R bps. 
- Cuando M nodos tiene que trasmitir, que la tasa media de trasmicion sea de R/M bps. 
- Es un protocolo decentralizado (no hay un nodo maestro)
- Un protocolo simple

## Protocolos de particionamiento del canal
Para comenzar tenemos a *TDM* y *FMD*, donde el primero divide en tiempo en unidades y a estas las divide en la cantidad de emisores que hay en el canal, ejemplo M. Por lo que cada emisor tiene el canal para trasmitir libremente durante 1/M tiempo de la unidad. FDM en vez de partir por tiempo, parte el canal en frecuencia, de esta forma cada emisor tiene una m-avas partes de la banda. 
Ambos tiene el problema que si solo un nodo esta trasmitiendo se desperdicia capacidad de trasmicion media (solo una 1/M del tiempo que podria o un 1/M del ancho de banda). Aunque tiene la ventaja que no hay colicion. 

Luego tenemos otro protocolo de particionamiento de canal conocido como *CDMA*, donde cada emisor elige con cuidado un codigo. COn ese codigo codifica los mensajes. Si estos codigos se eligen con cuidado, los nodos tiene la capacidad de trasmitir simultanemanete y conseguir que los receptores decodifiquen correctamente los bits de datos codificados, decodificado los bit con el codigo con el que fueron codificados.

## Protocolos de acceso aletorio
En estos protocolos de acceso, cada nodo trasmite a la maxima velocidad, pero cuando se da una colicion, todos los nodos implicados retrasmiten sus tramas hasta que se logre trasmitir sin colicion. Pero entre antes de volver a enviar espera un tiempo aletorio. Con este margen puede ocurrir que la diferencia de tiempo sea suficiente para que la trasmicion se de con exito. 

###  ALOHA con particiones
Es uno de los protoclos de acceso aletorio mas simple. Adjunto abajo un resumen del funcionamiento del protoclo que esta re bien explicado, pero no es todo lo que dice el libro sobre esto. 
![[Pasted image 20221115204303.png]]


Una ventaja que tiene ese protoclo es que si solo hay un nodo trasmitiendo, tiene una velocidad total del enlase. Es decentralizado (cada nodo decide su metodo de deteccion de colicion y probablidad de re-envio independiemente ), hay versiones de ALOHA sin particiones, lo que hace que no tiene porque estar sincronizados). Por ultimo es un protoclo extremandamente simple. 

Hay dos preocupaciones en cuanto a la eficiencia:
- Las particiones desperdiciada por la colicion
- Las particiones desperdiciadas porque nadie envio nada

#### Def 
Se define *particiones con exito* a las particiones donde solamente hay un nodo trasmitiendo y por ende la trama se pudo trasmitir con exito. La *eficiencia* se pide como la fraccion de parciones con exito en un periodo largo y con un gran numero de nodos activos con varias cosas para emitir


Si se asumen ciertas condiciones (por ej que siempre se trasmite con probabilidad p y que siempre hay cosas para emitir) . Se consigue la formula de eficiencia $N.p(1-p)^{N-1}$ . Para encontrar la eficiencia habia que encontrar `p`. Lo que se hace es hacer tender N a infinito y se ve el maximo, que segun el libro es $1/e = 0.37$  


### Protoclo Aloha (sin particiones)
Este fue el algoritmo que originalmente se diseño. No se requiere de sincroniacion con los demas nodos para las particiones. 
Algunos cambios:
- Cuando un datagrama baja de la capa de red, se los tramite inmediatamente 
- Si luego de haber terminado de emitir el paquete se detecta colicion, se lo retrasmite inmediatamente con probailidad `p`. En caso que no se deba retrasmitir se espera el tiempo que se demora en trasmitir una trama [duda ¿esto es constante?]
Supongamos que a mi me lleva un tiempo 1 trasmitir mi trama y se envia en el instante `t`. Ningun nodo puede comenzar a enviar su trama entre entre $[t-1 , t + 1]$ Lo que hace que la eficacia de este aloha sea la mitad que el de particiones. Osea una eficacia de $1/{2e}$ . 
![[Pasted image 20221115212258.png]]

### Acceso multiple con sondeo de portadora (CSMA) y deteccion de colisiones (CSMA/CD)

Ninguna de las dos veciones de Aloha analiza si hay otros nodos trasmitiendo al momento de trasmitir. Tampodo deja de emitir aunque otro nodo colicione con la trama que actualmente esta enviado. 
Se introducen nuevas reglas a la familia de protoclos *CSMA* y *CSMA con deteccion de coliciones* (CSMA/CD). Un par de estas reglas son las siguientes: 
- `Sondeo de portadora`: Cada nodo escucha el canal anted de trasmitir, Si ya hay una trama de otro nodo en el canal, se espera un intervalo de tiempo (corto) antes de volver a sensar e intentar trasmitir. 
- `Deteccion de coliciones`: Si un nodo que esta trasmitiendo, detecta que otro nodo esta trasmitiendo una trama diferente a la suya, deja de trasmitir y espera un tiempo antes de volver a intentarlo. Osea no sigue emitiendo una trama que ya fue colicionada. 

Es importante contar con los dos mecanismos, ya que mientras mayor sea el *retardo de propagacion*, mayor sera la posibilidad que dos nodos con el sondeo de portadora no detecten que hay otro trasmitiendo, y cuando lo hagan las dos tramas colisione.   

Cuando se cuenta con la deteccion de coliciones, el *adaptador de red* no solamente envia la señal, sino que mientras se esta trasmitiendo se monitoriza el canal en busqueda de señales procedentes de otros adaptadores, en caso de encontrarla se cancela la trasmision y luego de un tiempo se vuelve a intentar 
![[Pasted image 20221115215112.png]]

Como se menciono una vez que se detecta la colicion hay un tiempo antes que se vuelva a intentar, a este tiempo se lo conoce como *backoff*, el cual claramente es aletorio porque sino las tramas volverian a colicionar. 
El tema es elegir bien ese tiempo de forma tal que el periodo sea *menor cuando el numero de nodos que colicionan sea pequeño y mayor cuando el numero de nodos que colicionan es mas grande.*

#### backoff exponencial binario 
La forma en la que por ejemplo ethernet soluciona esto con el algoritmo *backoff exponencial binario.* 
La idea es simple, Tenemos un conjunto de naturales con el rango $A_n=[0, 2^{n}-1]$ donde $n$ es el numero de coliciones que se ha dado en la trama hasta el momento. Cada vez que se da una colicion se aumenta el $n$ en uno (no se aumenta por ensima de $n=10$), y se elige $K$ de forma aletoria dentro de ese conjunto ($A_n$). Notar que se elige $K$ de un conjunto que va creciendo de forma exponencial, por eso se llama "exponencial binario". Luego Ethernet espera $K.512$ periodos de bit, el cual es el tiempo que le llevaria al emisor colocar esos bit en el canal. Por ejemplo, si K = 2 y en enlase tiene una velocidad de 100Mbps, entonces se espera de unos 10,24 ms antes de volver a analizar comenzar nuevamente el proceso de sondeo del enlase y trasmision)


#### Eficiencia de csma/cd
- Cuando el nodo esta solo tiene toda la velocidad del canal. 
- Se define como la fraccion de tiempo (a largo plazo) durante que las tramas estan siendo trasmitidas al canal sin coliciones cuando exiten u ngran numero de nodos activos, cada unode ellos con una grancantidad de tramas para enviar. 
- La formula es la siguiente 
![[Pasted image 20221115222244.png]]
-Si ($d_{prop} \rightarrow 0$ o $d_{trans} \rightarrow \infty$) $\Rightarrow$ $eficiencia \rightarrow 1$    

## Protocolos de toma de turnos

Es verdad que tanto ALOHA como CSMA (o CSMA/CD) nos dan una velocidad del enlase total cuando solo hay un nodo, pero no distribuye equitativamente la banda del enlase entre los nodos activos. Es por eso que exiten los protoclos de toma de turnos. 

### Protocolo de sondeo
Hay un nodo maestro que sondea a cada uno de los nodos del enlase en turnos rotatorios. Luego este nodo le informa a cada nodo cual es el numero maximo de tramas que puede enviar, y asi sigue de forma ciclica. 
El protoclo de sonde elimina las coliciones y las particiones vacias. Por lo que se tiene una mayor eficiencia. 
Pero tiene dos grandes desventajas, la primera es un *retraso de sondeo* (retraso de tiempo requerido para indicarle a un nodo que puede trasmitir), y otro fallo es que si el nodo maestro falla cae toda la comunicacion. 
Blutooth funciona con este sistema. 

### Protocolo de paso de testigo
A diferencia del anterior no se cuenta con un nodo maestro, se posee una *trama de tamaño pequeña especial* conocida como *testigo*. Que se intercambia entre los nodos de un determinado orden. Cuando un nodo tiene al testigo emite sus tramas hasta el numero maximo de estas o hasta que ya no tenga mas. Luego envia el testigo al siguiente nodo. 
Esto es un sistema muy eficiente y decentralizado.
Tiene el fallo que si un nodo falla o si se pierde la trama, todo el sistema falla y se tiene que iniciar un proceso de recuperar al testigo para que este vuelva a circular. 

## Caso de estudio: DOCSIS
En este caso se convinan los 3 estilos de algoritmos de acceso multiple, es acceso a internet por cable. Estos son todas las caracteristicas de funcionamiento:

- Se utiliza FMD para dividir en canal en canales de subida y canales de bajada. 
- Como todo el contenido de descarga solo se emite desde el CMTS, no hay problemas de colicion en este canal. 
- Para en canal de subida mutlples nodos puede considir en su canal de subida, es por eso que el CMTS divide en intervalos de tiempo, que a su vez tiene mini-particiones. 
- El CMTS le concede permiso a los modems a trasmitir sus tramas de subida en determinados mili-particiones. Este permiso es explicito a cada modem.
- Para pedir permiso de trasmitir, el modem tiene que enviar un mensaje por el canal de subida al CMTS, eso lo puede hacer durante determinados periodos especiales de mensajes de control, enviado su solicitud mediante mensajes MAP.
- Estos mensajes si pueden colicionar, en caso de un router no recivir un mensaje de control que le da permiso para enviar mensajes (ese mensaje le llega por el canal de baja), asume que el mensaje coliciono y utiliza la tecnica de backoff exponencialmente binario para saber cuando debe volver a enviar su trama de solicitud. 