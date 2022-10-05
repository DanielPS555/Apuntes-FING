# BitTorrent

BitTorrent es uno de los protocolos P2P mas conocidos.
Fue diseñado para la descarga de archivos, por lo que los *peer* de un *torrent* descargan *fragmentos*, genralmente de un tamaño de 256KB.

Cualquier peer puede dejar la descarga en cualquier momento, y regresar y terminar su descarga con los fragmentos restantes.

## Funcionamiento de BitTorrent
Cada torrent tiene un nodo (de infraestructura) llamada *tracker*, cada peer se registra ante el tracker, y le notifica periodicamente que sigue en el torrent. 

Cuando un nuevo peer se une al torrent, el tracker selecciona aleatoriamente un subconjunto de peer y le devuelve la IP de cada uno de estos. 

Luego el peer intenta estableser una conexcion TCP con cada uno de ellos, con quienes lo consigue se llamaran *peer vecinos*.

Cada un tiempo, el peer le pregunta a sus pares vecinos por su *lista de fragmentos*, que es la lista de fragmentos que actualmente ya tiene descargados. La idea es que nuestro peer intente conseguir los fragmentos que el no tiene pero alguno de esos peer si tiene. Tambien otros peer van a pedirle a nuestro peer por fragmentos que nosotros tenemos. Es por eso que hay que contestar a dos preguntas clave:
1. `¿Que fragmentos debemos solicitar a nuestros vecinos:`
	En base a la lista de fragmentos de nuestros pares vecinos, pediremos primero los *fragmentos menos comunes*, con el fin de aumentar el numero de copias de este y se pueda distribuir mas rapido en la red.  
2. `¿A cuales peer debemos responder con nuestros segmentos?`
	Nuestro peer va a estar sensando el numero de bits que recive, cada 10s va a elegir a los 4 peer que le suministra a mayor velocidad, y solamente a esos peer les va a enviar los paquete que soliciten. A estos peer se los conoce como *peer no filtrados*, cada 30s eligue alazar 1 peer, al cual le comienza a enviar fragmentos, se lo conoce como *peer no filtrado de forma optimista*. Al hacer esto puede ser que ese peer nos comienza a responder con segmentos a una velocidad que los otros 4 peer no filtros, en cuyo caso ese peer asiende a esta lista. Al resto de los vecinos de los conoce como *peer filtrados*. 
	La seleccion aleatoria permite que los nuevos peer tambien puedan conseguir datos. 
	
A este mecanismo se lo conoce como *tit-for-tat*.

> Con este mecanismo los pares que suministran datos a velocidades compatibles tienen a emparejarse. 


