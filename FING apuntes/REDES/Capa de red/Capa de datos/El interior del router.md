La primera funcion que vamos a ver del router es su *funcion de re-envio* (capa de datos)

Se puede dividir una aquitectura generica del router en 4 partes:
- `Puertos de entrada:` Tiene 3 funciones
	1. Brindar un enlase *fisico* en un router el cual se conecta al enlase
	2. Una capa de enlace encargada de interoperar con la *capa del enlase* del otro dispositivo. 
	3. Lee la informacion entrante, si es un paquete de un protoclo de enrutamiento lo re-dirige al al *procesador de enrutamiento* y si no utilizando la *tabla de re-envio* lo dirige a un puerto de salida
- `Entramado de conmutacion:` Conecta los puertos de entrada y de salida 
- `Puerto de salida:` Tiene tambien las dos primeras funcionalidades descritas para los puertos de entrada. Y Ademas almacena los paquetes recibidos den entramado de conmutacion, que luego emitira 
- `Procesador de enrutamiento:` Se encarga de ejecutar los *protocolos de enrutamiento*, *mantiene las tablas de enrutamiento*, *mantiene la informacion asociada del estado de los enlases* y *calcula la tabla de re-envio*. Luego si es un router SDN este procesador se encarga (por ejemplo) de comunicarse con el controlador remoto y obtener las tablas de re-envio. 

Por lo componentes relacionados con el plano de datos (los puertos y en entrelazado de conmutacion) se implementan totalmente en hardware por un tema de velocidad. Mientras que el procesador de enrutamiento (plano de control) se implementa por software. 


![[Pasted image 20221019163055.png]]

Hay dos tipos de re-envio:
- *Reenvio basado en destino* (destination-based forwarding): El re-envio se realiza unicamente considerando la dirrecion de destino
- *Reenvio generalizado en destino* (generalized-based forwarding): El re-envio se realiza considerando otros factores, un ejemplo podria ser la ip de origen. 


## Prosesamiento del puerto de entrada (reenvio basado en destino)

En la busqueda realizada en los puerto de entrada se utiliza la tabla de reenvio para decidir a que puerto de salida hay que dirigir el paquete. 

La tabla de reenvio puede ser calculada por el procesador de enrutamiento o un controlador externo. De todas formas es copiada en las *targetas de linea* (de los puertos de entrada) por un bus especializado. 

En la tabla de re-envio se guarda la asociacion de la interface de red y el prefixo a ser utilizado. Como se muestra en la siguiente foto:

![[Pasted image 20221019163143.png]]

Se elige la interface asociada al prefijo mas largo que coniside pletamente con la dirrecion de destino del paquete. 

Par ala busqueda en la tabla de re-envio se suele utilizar memorias TCAM, que devuelven un resultado en un tiempo parcilamente constante. 

Los paquetes que van llegando al puerto de entrada pueden no ser inmediantemente enviados al *entramado de conmutacion* si el mismo esta siendo utilizado (esto depende del diseño). Para esos casos se tiene una cola en el pierto de entrada 

El procesamiento del puerto de entrada corresponde a una abstracion llamada *correspondencia mas accion* en la cual se busca la correspondencia de un elemento y dependiendo del mismo se hace una accion. 

### Otras acciones del procesamiento del puerto de entrada
1. Realizar el procesamiento fisicio y de la capa de enlase
2. Comprobar los campos de numero de version, checkSum o tiempo de vida. Y en algunos casos modificarlo. 
3. Actualizar contadores para la gestion de red (por ejemplo el contador de datagramas IP recibidos)

## Conmutacion
Aqui tenemos algunos metodos para la conmutacion realizada en el *entramado de computacion*
1. `Conmutacion via memoria:` Una CPU (antes era el propio prosesador de enrutamiento, ahora pueden ser los procesadores de linea de los puertos de entrada) movian los paquetes a una dirrecion espesifica de la memoria donde estan los buffers de los puertos de salida. Esto no permite que se puedan enviar dos paquetes a la vez.
2. `Conmutacion via Bus`: Todos los puertos de entrada y salida estan conmunicados bajo un bus comun, uno de ellos envia un paquete con una etiqeuta delante que indica el puerto destinatario. Solo ese bus lo atiene. Este sistema funciona mejor ya que no hay una CPU o memoria interviniendo, pero la trasmicion por el BUS sigue acotada a un paquete a la vez.
3. `Conmutacion via de red de interconexcion`; Se utiliza un *conmutador malla*, donde se forma una red entre los puertos de entrada y los puertos de salida. cada par (entrada, salida) tiene un puerto de corte que es administrado por un controlador del conmutador (inplementado en el propio entrlazado de conmutadores). Por lo que el conmutador de malla es *no bloqueante* a menos que mas de un paquete al puerto de salida.

Se puede mejorar el problema de solo poder enviar a una salida por vez si se utiliza un diseño con *multiples etapas*. Y se puede mejorar la velocidad utilizadando *entramados de conmutacion en paralelo*, donde se divide el paquete en segmentos y se envia cada uno en paralelo. 


## Colas 
La ubicacion de las colas en los routers (que son las famosas colas que generaban los retardos de cola) se encuentran en los *puertos de entrada* y en los *puertos de salida*. Es aqui donde se da la verdadera perdida o retraso de los paquetes.

Las *colas de entrada* son necesarias cuando la velocidad del entrelazado de conmutacion no es suficiente para trasmitir todos los paquetes que han llegado a los puertos de entrada. 

Mientras que las *colas de salida* son necesarias si nos llegan a los puertos de salidas mas paquetes de los puertos de entrada que los que podemos enviar.  

### Bloqueo HOL (bloqueo de cabeza)
Por lo general las colas de entrada son FIFO, por lo que si un paquete en la cabeza de la cola de entrada tiene como destino un puerto de salida que actualmente se le esta enviado paquetes (por otros puertos), todos los paquetes detras de el estaran bloqueados, incuso aunque el puerto de salida al que se le asigno ese libre.  

### Politica de eliminacion en los buffers
Cuando un buffer se llena tiene dos posibles acciones:
1. *Eliminacion del ultimo:* elimina el ultmo paquete que llego a la cola
2. Elimina uno o mas paquetes que ya estaba en la cola para hacer espacio. Tambien se puede marcar congestion en la cabecera IP de los paquetes de la cola con el fin de limitar al emisor, por ejemplo TCP que implemente control de congestion asistida por la red.

### Planificador de paquetes 
Debido a la exitencia de colas, tenemos que usar un *planificador de paquetes* . Mas adelante se veo eso 

### Tamaño del buffer
Sea el RTT el tiempo promedio de ida y vuelta, y C la capacidad del enlase. Antes se pensaba que el tamaño optimo era $RTT.C$ , pero si hay N flujos TCP, se puede reducir el tamaño a $\frac{RTT.C}{\sqrt{N}}$  





## Dudas
- [ ] ¿Que diferencia hay entre la tablas de enrutamiento y la tabla de re-envio?





285 -324