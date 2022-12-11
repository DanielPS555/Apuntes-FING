Los host y routers tiene dirrecion de capa de enlase ademas de la dirrecion de la capa de red. 
Luego vamos a ver porque son necesario tenerlos a ambos.
Tambien se va a ver el protolo *ARP* para traducir dirreciones de capa de red en dirreciones de capa de enlase. 

## Dirreciones MAC
Las dirreciones de capa de red se asignan a los adaptadores de red. Osea que si una computadora tiene varias interfaces, va a tener varias dirreciones ip y variads dirreciones de capa de enlase. 

**Importante:** 
- Las interfaces de los switch no tiene asociada a sus interfaces una dirrecion de red. Esto se hace asi para que el switch sea transparente para el host o router. 

A las direcciones de la capa de enlase se las suele llamar de varias formas, *dirrecion LAN*, *dirrecion fisica* o mas comunmente *dirrecion MAC*. Estas dirreciones tiene 6 bytes de longitud. 

Se diseñaron las MAC para ser fijas por adaptador, pero se puede modificar esto por software. Osea no exiten dos adaptadores con la misma dirrecion MAC. Esto es asi porque los primeros 24 bit son por compañia, y deben ser comprados a la IEEE. Los 24 bits menos significativos los administra la empresa como quiere. 

La dirrecion MAC tiene una *estructura plana, a diferencia de la IP, la dirrecion IP es jerarquica* (parte red, parte host), y *esta se modifica dependiendo de la posicion de la persona, mientras que la MAC nunca cambia*. 

Cuando se quiere enviar un mensaje desde un host a otro por medio de la red LAN, el emisor pone la dirrecion del otro adaptador como destino. Hay veces que los switches en vez de enviar una trama al correspondiente host, la termina enviado por todas sus interfaces. Es por eso que el host de destino cuando recive una trama debe revisar que la dirrecion MAC de destino sea la suya. Si no es la suya descarta el paquete y no lo suba a capa 3. A menos que tenga la *dirrecion de difucion* que es una dirrecion MAC especial FF-FF-FF-FF-FF-FF.

## Protocolo ARP
Este protoclo se encarga de hacer la *traducion* entre dirreciones IP y dirreciones MAC **dentro de la misma subred**, no funciona fuera de la subred. La necesidad de este servicio es como carajo hace sino un host enviarle un mensaje a una PC dentro de la subred si no sabe la MAC. Bueno ARP se encarga de eso. 

Cada host y cada router se guarda en su tabla ARP una entrada por cada ip, asociada con la dirrecion MAC de la interface y un TTL. Por lo general los TTL son de 20min.

Cuando un host tiene que enviar una trama a una MAC determinada, si la misma no se encuentra en la tabla ARP, lo que se hace construir un paquete especial llamado *paquete ARP*, el cual tiene la MAC e IP del emisor y la IP del receptor. Para la MAC de destino se usa la *dirrecion de difucion*. 
ARP de consulta y respuesta tiene el mismo formato.
Como el mensaje va con la dirrecion de difucion, llega a todos los adaptadores de la subred y es procesados por todos ellos. Pero solo el adaptador que tenga como IP la buscada sera quien responda con *paquete ARP de respuesta*. Aunque en este caso no se envia esta respuesta a la dirrecion de difucion, sino a quien haya emitido la pregunta ARP. 

La ubicacion del protoclo ARP en el stack de protoclos se podria ubicar entre la capa de enlase y la capa de red. Es una mecla porque va dentro de una trama, pero es de red porque tiene campos de la capa de red como la ip. Como siempre, todo una mierda. 

![[Pasted image 20221201230858.png]]


## Envio de un datagrama fuera de la subred
[Mirar el ejemplo del libro que esta muy bueno]