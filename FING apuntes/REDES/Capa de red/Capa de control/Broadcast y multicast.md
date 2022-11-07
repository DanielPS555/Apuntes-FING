## Forma de emitir un broadcast
Enviar paquete desde una dirrecion a todos los otros nodos es super ineficiente. Pensar que un mismo paquete pasa varias veces por el mismo destino. Ademas que el origen deberia saber la dirrecion de cada destino. Mala idea. 

Hay  otros encares:
- `Flooding`: El vecino recive una copia de un paquete brocast y se la envia a todos su vecinos (menos de quien lo recivio). Genera los siguientes problemas: *cycles*: los paquete comienzan a llegar en ciclos y *broadcast storm*: si un nodo tiene mas de tres nodos conectados, duplicara el numero de paquetes brocadcast, y si hay ciclos el numeros de estos paquetes aumentara muy rapidamente.
- `Controlled flooding`:  Ahora los nodos tiene que poder elegir cuando duplicar o no un paquete. Hay varias formas de hacer esto : 
	- `Sequence number controlled flooding:` A la hora de emitir un paquete, el emisor le pone un numero de secuencia y un dirrecion (la del emisor, ej la ip). Luego los demas nodos tiene una lista de los numero de secuencia que hay resivido, si no lo recivieron lo re-envian, en caso contrario no. 
	- `Reverse path forearding (RPF)`: Solo re-envio los paquete broadcast que me llegan de un nodo que seria el mismo que yo usaria para enviarle al nodo de origen un mensaje. Si llega de cualquier otro nodo no lo re-envio.  Esta tecnica evita broadcast storms. ![[Pasted image 20221106035554.png]]	
- `Spanning-tree`: Un *spanning tree* es un arbol en el grafo que cubre a todos los nodos. Y si hay un costo asociado a cada arista, un *minumun spanning tree* es el arbol que la suma de sus costos es el menor. Para su uso se debe primero crear el spanning tree en la red, y luego que cada nodo sea consiente cuales de sus vecinos integran el spanning tree. Luego una vez que le llega un mensaje de uno de ellos envia el mensaje al resto (de los vecinos de spanning tree) sin precuparse de ciclos. El problema es crear y mantener el abrol. Un algoritmo conocido para la construccion de esos arboles se llama *center-base-approach* , donde se elige un nodo *core*, luegos todos le envian paquetes a el, cuando el paquete llega a algun nodo que sea parte de arbol, ese entiende que ese nodo es su padre y termina su busqueda, osea se genera una rama por asi decirlo, por lo que no se requiere llegar hasta el core. Estos mensajes que se envian estos nodos para formar la ruta se llaman *tree-join message*. ![[Pasted image 20221106041146.png]]

## Multicast
Ahora vamos a comunicarnos no con todos los dispositivos (broadcast), Sino que con un conjunto de ellos. Por lo que surgen inmediatamente dos problemas:
1. ¿Como identificamos los receptores de esta multicast?
2. ¿Como identificamos los paquetes que van hacia este conjunto?

La forma en la que vamos a identificar los paquetes de un multicast va a hacer con un *adress indirection*. Osea un unico identificador para grupos. En particular en internet es una ip de clase D. 
El grupo asociado a esa ip se le llamara *multicast group*. 
Un problema claro es como convivir con la Ip unicast y la (o las ) multicast que se tenga. Todos los manejos de eso y mucho mas es responsabilidad del protoclo *IGMP*. Tambien abra algoritmos de routeo multicast. 

El funcionamiento de IGMP es simple. El router envia a los host de una interface determinada un mensaje IGMP de tipo *membership_querry*, Luego ante ese mensaje o iniciativa propia del host le responde al router con un mensaje IGMP de topo *mermbership_report* donde le informa a los grupos que esta unido. Luego el host puede enviar un mensaje IGMP *leave_group* para salir del multicast o si no responde a los mermbership_querry, tamien se lo saca via timeout. 

### Soft state
Un protoclo es soft-state si un participante es removido via un timeout por no enviar mensajes de refresco. Este tipo de protocolos simplifican el control, y ademas permite recuperar el estado ante un fallo inesperado. Pero claramente tiene un control de estado mucho menos presiso. El primero que hablo de esto fue Clark 1988. 


