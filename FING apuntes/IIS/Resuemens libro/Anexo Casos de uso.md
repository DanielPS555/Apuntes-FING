#### Caso de uso 
- Tiene un formato simple donde los usuarios y desarroladores pueden trabajar juntos
- Durante la definicion del caso de uso se pueden definir pantallas de usuario
- Se puede usar en el diseño y testing
- Ventajas:
	- Permite ver facilmente la interacion del sistema con los actores (usuarios o otros sistemas)
	- Muy utiles cuando la implementacion se va a hacer POO y con UML
- Desventajas: 
	- No son buenos para describir requerimientos no funcionales 
	- Malos cuando no hay usuarios (por ejemplo un schedule)

> Los casos de uso describen una secuencia de interacciones entre un sistema y un actor externo que resultan en un resultado de valor para el actor

- Cada esenario comprende una instancia de uso del sistema. Un *caso de uso contempla un conjuto de escenarios relacionados*. 
- Son independientes al metodo de diseño y lenguaje de programacion

##### Actores 
SOn las personas o otros sistemas que interactuan para realizar el caso de uso. **No es un actor nuestro sistema**

##### Digrama de casos de uso 
![[IISCap4_1.png]]

La caja representa el entorno de nuestro sistema. Puede haber CU fuera de ella. 

##### Elementos esenciales de un caso de uso 
- Identificador unico 
- Brebe descripcion
- Pre-condiciones
- Pos-condiciones
- Una lista enumerada de pasos que muestra la secuencia de interracion entre actor y sistema. 
 A eso se lo llama *flujo normal y flujo alternativos*. El flujo principal muestra la secuencia mas comun para la ejecucion del caso de uso. Los casos alternativos describen escenarios alternativos al principal (casos particulares, excepciones)
 Se los puede representar graficamente o por texto. 
 **Importante:**
	- NUNCA puede comenzar un flujo con el sistema. Lo comienzan los actores. 
	- Cada paso tiene que ser lo mas simple posible
	- Cada linea identifica al actor o sistema que lo hace.
- Un caso de uso con id, descripcion,  pre y post condiciones se dice que tiene una escritura de *alto nivel*
- Si ademas tiene los flujos normales y alternativos se dice que es un *caso de uso expandido*

##### Relaciones entre los CU
- *Inclusion*: Un CU llama a otro, y solo sigue si el CU que se llama "termino correctamente". Va "include" delante del CU.
- *Extencion* : Se utilizan para esenarios alternativos complejos. Un fragmento de un CU que extiene, agrega comportamiento a otro CU. Ese CU se cumple si una ciertca condicion es verdadera en algun punto espesifico del CU a extender. A este punto de lo llama *punto de extension*. 

##### Estategias para identificar CU
- Identificar actores, luego procesos, y definir CU para las acrtividades que interactuan con esos actores y sistema
- A partir de ecenarios espesificios que inlustran procesos, generarlizarlos en CU identificando a sus actores 
- identificar eventos externos a los cuales el sistema debe responder, ver los CU y actores relacionados a esos eventos.
- Identificar entidades de dato que requieren de CU para alta, lectura, actualizacion, borrado, etc. 