# Principio del control de congestion 
En la practica, la mayoria de las de las perdidas de paquetes se ven devidas a desbordamiento de los buffers de los routers de la red. Es por eso que se requieren de controles de congestion con el fin que los clientes tengan cuidado de no saturar la red en demacia. O al menos no contribuir a este saturamiento. 

## Costes de la congestion 
A continuacion numero alguno de los principales costes que tiene la congestion:
1. Grandes retardos de cola experimentados cuando la tasa de llegada de los paquetes se aproxima a la capacidad del enlase. 
2. El emisor tiene que realizar retrasmiciones para poder compenzar los paquetes perdidos a causa del desbordamiento del buffer.
3. Las retrasmiciones innecesarias del emisor causadas por retardos largos pueden llevar a que un router desperdice ancho de banda en reenviar copias innecesarias de un paquete 
4. La capacidad de trasmicion empleada en cada uno de los enlases necesarios para encaminar el paquete hasta el punto donde se perdio termina por ser desperdiciada.

## Metodo de control de congestion 
Las tecnicas de congestion pueden trabajar junto o sin la capa de red. Si trabajamos con la red podemos usar el *Control de congestion asistido por la red* y sino podemos usar el *Control de congestion terminal a terminal *
- *Control de congestion terminal a terminal*: Eso se basa unicamente en la observacion del comportamiento de la red. Si un paquete si el temporizador espira o si se devuelbe un tripe ASK, se baja el tamaño de la ventana. 
- *Control de congestion asistido por la red*: Aqui la capa de red da asistencia, donde la misma de alguna forma intenta notificar al emisor de la sobrecarga. Hay dos formas de hacer esto:
	- *Retroalimentacion directa*: es el mismo router el que nos envia un mensaje diciendo que esta congestionado 
	- *Retroalimentacion a travez del receptor*: El router marca al paquete con un bit diciendo que esta congestionado, si un paquete le llega al receptor con este bit activado, el mismo receptor le envia un mensaje al emisor notificandole que el la red esta congestionada. 
