- A diferencia de la capa de transporte y de aplicacion, existe un componente de la capa de red en todos y cada uno de los hosts y routers de la red. 
- Hay dos planos. 
	- *Plano de control*: Esto se encarga del modo en que se enruta un datagrama a lo largo de una serie de routers. Osea el trayo extremo a extremo. 
	- *Plano de datos*: Las funciones que implnetan como se determina el enlase de salida del router para los datagrama
- Los protocolos de ambas capas estan claramente separados. Incluso los servicios de la plano de control pueden estan implemenetados en lo que se lo conoce como un controlador. 

> La función principal del plano de datos de cada router consiste en reenviar los
datagramas desde sus enlaces de entrada a sus enlaces de salida; la función principal del plano de
control de la red consiste en coordinar estas acciones de reenvío locales de cada router individual, de
modo que los datagramas terminen transfiriéndose de extremo a extremo, a lo largo de series de routers
comprendidos entre los hosts de origen y de destino.

## Funcionalidades de la capa de red

**Importante:** La funcion principal de la capa de red es "Transporta paquetes desde un host
emisor a un host receptor"

Para realizar esta tarea se distingen dos funcionalidades clave.

Una cosa curiosa es que los dos planos estan tan separados que podria ser una opcion ponerlos en lugares fisicos diferentes. 

### Reenvio (Forwarding)
Su principal funcionalidad es el re-envio de datos que llegaron de algun enlase del router, *No es la unica funcionalidad del plano de datos*. Tambien se puede retener un paquete o multiplicarlo. 

Por lo general esta accion demoroa un muy poco tiempo. La decicion se realiza basandose en la *tabla de reenvio*.  


### Enrutamiento
Son los protocolos que se encargan de estableser la ruta desde un host a otro host. Se los conoce como *Algoritmos de enrutamiento*. 
Las *tablas de reenvio* son calculadas entre los routers utilizando protoclos de enrutamiento, por medio de *mensajes de enrutamiento*. Aqui tenemos un ejemplo como se conectan las dos planos de esta capa. 

## Limitantes de la capa de red

La capa de internet (que esta en la capa de red) solamente tiene un servicio con el nombre de **best-effort**. Osea no garantiza la entrega, ni el orden, ni la congestion, ni el retardo. Hay otras propuestas pero internet demuestra ser el big boss.

## Comentarios

### SDN
Hay veces que los algoritmos de enrutamiento no son calculadas por el mismo router, sino que son defindia por un software. A estas implementacion se las llama como *red definida por software (SDN)*. 


### Conmutador de paquete
> Reservaremos el término conmutador de paquetes para referirnos a un dispositivo de conmutación
   de paquetes general, que transfiere un paquete desde la interfaz del enlace de entrada a la interfaz del enlace de salida

Podemos diferenciar dos tipos de conmutadores: 
- *Conmutadores de capa de enlase (switches) :* Toman su decicion  en base a la trama
- *Routers*: basan su desiscion en el cabesal del datagrama. 


