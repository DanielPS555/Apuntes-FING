# Pregunta 1

### Version 1

El plano de datos es el encargada de la funcion local de re-envio. En particular en base a la arquitectura recive los datagrama por los puertos de entrada, actualiza los datos de la cabecera que corresponda, consulta la tabla de re-envios y en base a eso redirige (cuando pueda) el datagrama a buffer del puerto de salida correspondiente. 

Por otro lado el plano de control de encarga determinar los routas por la cual los datagramas deberan transitiar por la red con el fin de llegar a su destino. Los algoritmos encargados de esose llaman protocolos de enrutamiento, reciviendo y enviando los mensajes necesarios para la ejecucion del mismo de los otros dispositivos que tambien tiene plano de datos y estan bajo un algoritmo de enrutamiento comun. Via un procesador de enrutamiento, este calcula la tabla de re-envio (o la obtiene de un SDN) con el fin de indicarle a los routers, la interface de salida para los datagrama con determinados prefixos.

La relacion principal es la tabla de re-envio, el plano de datos la consume para realizar su accion de redirrecion, mientras que el plano de datos es el encargado de generarla y introduciarla (en el caso del procesador de enrutamiento) en las lineas de entrada. 

### Version 2 
Omito 

### Version 3

# Pregunta 5

### Version 1
a) Los sistemas autonomos (AS) son esa una porcion de la red (conjunto de routers) administrada generalmente por la misma entidad con autonomia del resto de las AS, tanto a nivel administravio, topologia y enrutamiento. Eso les permite a cada organizacion (que se maneje con una AS o varias AS) tener control sobre su red, y al mismo tiempo mantener la informacion de ruteo interno del AS dentro del mismo, de esta forma se puede mantener. Ademas de la autonomia, esto permite manejar de mejor manera la escala de la informacion de ruteo de toda internet. Cada AS se identifica con un codigo unico cado por la ICANN. 

b) En enrutamiento Intra-AS es el enrutamiento interno del AS, esto permite enrutar dentro del AS, y al mismo tiempo permite que cada AS pueda usar el algoritmo de enrutamiento que considere mejor, o incluso algoritmos propios. Eso le da autonomia a los AS. 
Ademas la separacion de los AS permite mantener a raya la escala de las tablas de routeo de los ruters. 
Por ultimo, se tiene que separar las prioridades del enrutamiento inter-as y intra-as, en el inter-as tiene mas importancia las politicas entre los AS, por ejemplo a quien le puedo anunciar mis rutas, a quien no, por quien me conviene ir, etc. Mientras que en las intra-as el enfoque esta en la performance, no en las politicas. 
Por otro lado el enrutamiento inter-AS permite el anuncio de subredes por parte de los AS a otros AS, eso justamente es lo que permite uno se pueda conectar con servicios que viven en distintos AS. 

c) Tiene 4 criterios (en esta prioridad) para la eleccion de la ruta
1. Eleccion por politica local: Hay reglas que tienen los As para automaticamente descartar rutas anunciadas de otros AS. O darles prioridad. 
2. Se toma el As-PATH mas corto 
3. Criterio de la papa caliente (se busca el anuncio que tenga el NEXt-HOP con menor costo interno)
4. identificador BGP (esto lo saque de la solucion)

# Pregunta 6

### Version 1
Omito

### Version 2
a) La capa de red sera la encarga de la comunicacion host a host, utilizado para ello las dirreciones IP, las cuales son dirreciones logicas, dinamicas y lo mas importante jerarquicas, para esto mismo la capa de red tiene dos principales objetivos, el re-envio y el ruteo. La principal diferencia con la capa de enlase es que esta ultima tiene como objetivo la tranferencia de tramas entre dos nodos que estan dirrectamente conectados. Lideando en el medio con los problemas fisicos de los enlases que el resto de las capaz simplemente ignoran. 

b) En los enlases de difucion podemos tener multiples nodos trasmitiendo tramas al canal al mismo tiempo, lo que significa que a nivel fisico las señales de estas tramas puede colicionar y perderse. Es por eso que se presisa de una categoria de protocolos que administren el acceso y uso a ese enlase. Esta familia de algoritmos se llama *algoritmos de acceso multiple*, dentro de los cuales se dividen en 3 categorias.
- ``Por particion del canal``: Se particiona logicamente o fisicamente el canal. Por ejemplo de puede particionar por frecuencia o por periodos de tiempo. Esto permitr que se pueda trasmitir en simultanio, pero acotada su velocidad. 
- ``Por acceso aletorio``:  En estos algoritmos se emite el mensaje de forma aletoria, osea se elige con cuidado, pero no hay nada que fije que el tiempo de envio sea un determiado luego de una colicion. Tampoco tiene practicamente ninguna cordinacion con los demas enlases. 
- ``Por toma de turnos:`` Aqui tenemos que algo o alguien le da la potestad a un nodo de hacer uso exlusivo del canal para trasmitir un numero maximo de tramas. Luego se le asigna el permiso de trasmitir a otro nodo y asi sigue. Los casos mas comunes de esto es el *algoritmo de sondeo (pulling)* y por *paso de testigo (token)*.

### Version 3
Omito

### Version 4
a) Son transpartenes por dos motivos:
- Las interfaces de red de los switch no tiene MAC, por lo que el nodo que emite el mensaje en realidad no tiene ni idea si se lo esta pasado a un switch (o switches) o si dirrectamente al nodo. 
- Los switches son totalmente plug and play, eso siginficia que no requieren de ninguna configuracion o protoclo para poder operar dentro de la red. 
Ambas propiedades hacen que un switch se pueda integrar en una LAN, sin que nadie lo sepa. 

b) Falso, en realidad cuando a un switch le llega una dirrecion de destino desconocida realiza la tecnia de flooding, en otras palabra le envia a todas las interfaces (menos la de origen) la trama resivida. Ademas si hiciera esto no tendria sentido la transparencia, ya que quien responda la respuesta del ARP deberia saber quien fue el origen de la pregunta ARP, y por ende los switches deberian ser identificables en la LAN, lo que va encontra de la invisibilidad. 

c) Se puede hacer. Primero que nada hay definir 3 VLAN con LA MISMA NUMERACIONy elegir los puertos del switch para cada VLAN, luego deberemos configurar un router externo (o interno del switch) para la comunicacion entre VLAN si haci lo queremos. Lo importante de la pregunta es como conectamos los switch de forma tal que no se pieda la separacion de VLAN al pasar de un router a otro. La respuesta es con un *trunk port*. La idea de estos puertos es que conectan a los switches por un solo enlase por donde viajan las tramas de todas las VLAN, pero estos mensajes viajan con el protoclo 802.1q, el cual añade al cabezal ethernet dos campos espesificos para las VLAN, que identifican de que VLAN es cada trama, de forma tal que al llegar a otro router se sepa cuales son los puertos para donde se puede re-enviar,  

### Version 5

No se pueden hacer sin la figura. Igual esta muy buena la soluccion.