La funcion principal de un router es recibir las tramas y re-enviar las mismas a los puertos de salida correspondientes. 
El funcionamiento del switch debe ser *transparente* para los hosts y los routers. Por lo que cuando los nodos reciven/envian tramas, no tiene ni idea que habia uno o mas switches en el medio. 

Las interfaces de un switch de salida de un buffer puede recibir tramas mas rapido de las que las puede enviar por el switch, es por eso que se tiene *buffers* para almacenar estas tramas. 

Estas son algunas de las funciones del switch:

- El *filtrado* es la funcion de un switch que determina si una trama debe ser renviada a alguna interface o debe ser descartada 
- El *reenvio* es la funcion del switch que determina las interfaces a la que debe dirigir la trama y envia la trama a la interface correspondiente. 

Ambas funciones se realizan con la *tabla de conmutacion*. El formato de esta tabla tiene a priori 3 entradas: 
1. Dirrecion MAC
2. Interface del switch lleva hacia esa interface
3. Instante en que la entrada fue incluida en la tabla. 
La principal diferencia entre el re-envio por router y por switch es que una usa IP y otra usa dirreciones MAC.


## Funcionamiento del filtrado y re-envio del switch
Hay 3 posibles comportamientos segun los datos de la tabla de conmutacion. En base a una trama con una dirrecion MAC DD-DD-DD-DD-DD-DD recibida por la interface X. 
1. No hay ninguna entrada para DD-DD-DD-DD-DD-DD en la tabla, por lo que el switch re-envia copias a todas las interfaces salvo a X. 
2. Hay una entrada que asocia DD-DD-DD-DD-DD-DD con X. En ese caso el switch filtra el paquete y se lo descarta
3. Hay una entrada que asocia a DD-DD-DD-DD-DD-DD con una interface Y diferente de X. En ese caso se re-envia la trama a la interface Y.

Notar que si se cuenta con una tabla de conmutacion completa y correcta, entonces no se realiza ninguna difucion durante la trasmicion. 

## Auto-aprendizaje
Los switch son capaces de construir su tabla de conmutacion de forma automatica, dinamica y autonoma. A esta caracteritica se la llama *auto-aprendizaje*. No requiere de ninguna administracion ni protocolo para esta configuracion. 
1. La tabla esta inicialmente vacia
2. Por cada entrada recibida de una interface, se almacena de la dirrecion MAC del campo de dirrecion de origen, la interface de donde llego la trama y a la hora que llego [¿se pueden regitrar dos interfaces para la misma MAC?, supongo que no por el spanning tree]
3. Si no se recive ninguna dirrecion de origen en el *tiempo de envejecimiento*, entonces se borra la entrad de la tabla.
Los switches son dispositivos *plug and play* ya que no requierende ninguna intervencon de administraodres ni de usuarios [duda: serie plug and play un DHCP? Ahi si se requiere de un protoclo pero nada de los administradores]

Tambien se permite la comunicacion *full-duplex* y funcionan con *CSMA/CD*.

## Propiedades de la conmutacion de la capa de enlase
Hay varias ventajas de usar switches en vez de enlases de difucion.
- `Eliminacion de las coliciones`: En una red LAN construida con switches y sin hubs, no se desperdicia ancho de banda a causa de coliciones. Es por eso que la tasa maxima de tranferencia agregada de un switch es la suma de todas las tasas de tranferencia de lasinterfaces del switch. 
- `Enlases heterogenos`: Los switches puede tranabajar con interfaces que tengan diferente tipo de enlases y velocidades. 
- `Administracion`: Los swithces tiene una *seguridad mejorada*  , tambien facilita la tareas de gestion y recopilacion estadistica. Tambien permite detectar problemas con una interface y desconectarla internamente. 

## Switches frente routers 
Hay varias diferencias entre los switch y los routers. 
La mas obvia es que uno trabaja con dirreciones de capa de enlase y la otra con dirreciones de capa de red. Aunque hay casos en los que se pueden mesclarar mas si por ejemplo trabajamos con re-envio generalizado en los routers. 

### Ventaja y desventajas de los switches
#### Ventaja
- Son plug and play 
- Ofrece tasas de filtrado y re-envio altas: ya que tiene que procesar una capa menos
#### Desventaja
- La topologia activa esta restringida a un arbol de recubrimiento.
- Las tablas ARP puede crecer mucho 
- No tiene control ante las *tormentas de difucion*

### Ventaja y desventaja de los routers 
#### Ventajas
- Por lo general no se generan ciclos redundantes a menos que este mal configurado las tablas de routeo. Y por eso pueden usar mejores rutas desde el origen hasta el destino. 
- Proteccion mediante contrafuegos. frente a tormentas de difucion.
#### Desventajas
- No son plug and play 
- Tiene mayor tiempo de procesamiento

Es por eso que las redes pequeñas, con cientos de dispositivos se pueden ahorar los IP y pueden usar unciamente switches. En redes con miles de dispositivos se deberian utilizan routers para aislar las redes, controlar las tormentas de de difucion, calcular las rutas de forma mas optima. Y dentro de subredes claramente el uso de switch en vez de hub. 
![[Pasted image 20221116225608.png]]



 