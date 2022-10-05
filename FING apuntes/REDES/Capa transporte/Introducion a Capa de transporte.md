# Introducion a la capa de red 

La funcionalidad de esta capa es ampliar la funcionalidad de entrega de la capa de red, ahora la idea es brindar una comunicacion no solo entre terminales, sino entre *procesos*. 

Ademas la capa de transporte por medio de la capa de red, buscara solucionar alguno de los problemas mas importantes de las redes de computadora:
1. Como dos entidades pueden comunicarse de forma fiable a traves de un medio que puede perder o corromper los datos.
2. Como controlar la velocidad de transmision de las entidades de la capa de transporte con el fin de evitar, o recuperarse de las congestiones que tiene lugar dentro de la red. 

## Servicios de la capa de transporte

Todo protocolo que se encuentre en esta capa proporciona una *Comunicacion logica* entre procesos. Cuando se dice Comunicacion logica es que desde la perspectiva de la aplicacion, los host estan conectados directamente. Osea la aplicacion ignora todos los detalles de la estructura fisica que conecta a esos dos host. 

La capa de transporte convierte los mensajes de la capa de aplicacion en *segmentos*, añadiando su cabecera. Luego el segmento es pasado a la capa de red que se encargara del envio al otro host. 

Es de mencionar que ningun dispositivo dentre los dos host (salvo los proxy) modifica los datos de esta capa. 

La diferencia sustencial con la capa de red es que la capa de red propociona una Comunicacion logica pero entre host, no entre procesos. 

La capa de transporte se ve limitada a la capa de red, ya que funciona sobre ella. Pero de todas formas puede oferecer servicios que la capa de red no puede. Por ejemplo la capa de transporte tiene el protocolo TCP que es un protocolo de trasmicion de datos *fiable*, el cual esta montado sobre el protocolo IP que es *best effore* (Hace lo posible, pero no garantiza la llegada, ni que los datos no esten corrputos, ni que esten en orden), por lo tanto es *no fiable*.

Otro de los aspectos que puede implementar la capa de transporte son los *mecanismos de control de congestion*. Los cuales que cualquier conexcion que las implemente indunde de una cantidad excsiva de trafico los enlases que forman parte del camino de la red. 

Como comentamos esta capa extiene el servicio de entrega *host - host* a *proceso - proceso*, ese proceso se llama *multiplexacion y desmultiplexacion de la capa de transporte*. 


