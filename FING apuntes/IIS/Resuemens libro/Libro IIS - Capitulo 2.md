El *Software process* es un conjunto de actividades que llevan a la produccion de software. 

COmo ya se dijo no hay metodo de ingenieria de software generico para todo tipo de software, por lo que tampoco lo hay un unico Software process. Pero estos como ya se dijo siempren tiene 4 actividades  fundamentales : 
- Software specification
- Software development
- Software validation
- Software evolution

Cuando se descrive un proceso de software, tambien hay que describir otras cosas aparte de las actividades, alguna de estas son:
- *Que productos se va a tener como resultado de el proceso *
- *Los roles*. Los cuales descriven las responsabilidades de las personas involucradas 
- *pre y post condiciones que se deben cumplir para las actividades del proceso*. Ej: El consumidor debe haber aprobado los requerimientos antes del diseño de la arquitectura. Y un ejemplo de post condicion es que los modelos UML deben haber sido verificados luego del diseño de la arquitectura. 

#### Plan-driven process (proceso basado en planes) vs Agile process
En el primero el software process ya esta definido, y de definen metricas para medir el progreso contra el plan. 
En los Agile process, el plan es incremental, y se lo va diseñando a medida que se avanza en el proyecto.


## Software process models

Los *software process model* (o tambien Software development Life cycle) son implifaciones de un software process. Estos modelos solo muestran informacion parcial desde cierta perspecticva del modelo, pero no todo el proceso. 

Hay algunos process model que son muy generales, y que estos muestran el esqueleto del software proceess, pero no los detalles de las actividades. 

Vamos a ver 3 modelos: 
- *The waterfall model* 
- *Incremental development*
- *Integration and configuration*

En la practica se usa un poco de cada uno. 

Uno de los mejores intentos de un process univeral es uno llamado *Rational Unified process* (RUP).

### The waterfall model (modelo en casacada)

Fue el primer proceso de software publicado. Tiene multiples etapas las cuales son: 

![[Pasted image 20230304205500.png]]

- *Analisis de requermientos y definiciones:*: Se definen los requerimientos del cliente y las espesificaciones del sistema. 
- *Diseño de software*: En base a los requerimientos se identifica y describe la abstracion fundamental del sistema y el relacionamiento entre ellos.
- *Implementacion y testing unitario*: Aqui se implementa el software y se hacen pruebas unitarias.
- *Integracion y Testing del sistema*: Se integran los distintos programas desarrolados para completar el sistema. Luego se hacen prueba globales. 
- *Operativa y mantenimiento*: La parte mas larga, se pone el sistema en produccion, se hace mantenimiento arregando los errores no descubiertos hasta ahora, mejorando la implementacion de las unidades del sistema. 

En estos sistemas no se puede pasar a la siguiente etapa hasta haber terminado la anterior. 

Un problema grande con esto es que es mas caro hacer un cambio cuando el software esta terminado que cuando una pequeña parte del sistea esta construido. 

Pasa que en la operativa comun, las etapas de mescaln y en realidad una etapa anterior puede resibir un feedback de la siguiente en base a algo no previsto en la etapa previa, ejemplo que hay requerimientos faltantes o contradictorios. 

Si se conjelan los requerimientos o el resultado de una etapa previa puede casusar problemas a futuro. Por ejemplo dejar problemas que nunca se resuelven. 

En la realidad solo se puede utilizar este modelo para 3 tipos de sistemas: 
- *Embedded system*: Ya que la inflesibilidad de hardware hace que se tengan claro los requerimientos.
- *Critical systems*: Donde debido a la seguirdad que estos tiene se requiere de saber de todos los requerimientos para analisar. 
- *Grandes sistemas donde hay multiples organizaciones desarrolandolo*: Por lo general para que las empresas puedan trabajar de forma independiente, se requiere de los requerimientos completos de ante mano . 

### Incremental development 
En estos sistemas la idea es desarrolar una version inicial, conseguir feedback y luego evolucionar el software. 
Las etapas de espesificacion, desarrolo y validacion estan entrelazadas entonces. 

![[Pasted image 20230304212551.png]]

Este modelo se puede utilizar para los encares `plan-driven` y `agile`. En el caso que sea el primero se pueden definir cada iteracion desde un inicio, si es `agile` se pueden definir iteraciones iniciales, pero no las posteriores. 

> Incremental software development, which is a fundamental part of agile development methods, is better than a waterfall approach for systems whose requirements are likely to change during the development process

Este modelo tiene las siguientes *ventajas* que el modelo en casacada:
- Los costos de implementar cambios en los requerimiento es menor. 
- Es mas facil conseguir feedback de los clientes hacerca del desarrolo hecho.
- Es mas facil liberar software usable lo antes posible. Aunque no tenga toda la funcionalidad. 
Las desventajas (sobre todo a nivel de gestion) que tiene son: 
- Tiene mucho mas costo el testing, ya que se comienza a repetir pruebas.  
- No es visible el progreso global.
- La estructura del proyecto tiene a degradesarse a medida que se avanza en las nuevas versiones. En las metodologias agiles lo que se hace es hacer refactors periodicamente.

### Integration and configuration
Se basa en la reutilizacion de software ya desarrolado. 
Generalmente pasa informalmente, uno toma codigo que ya esta hecho y lo adapta a su caso. 

Este modelo se enfoca en la reutilizacion y configuracion. 
![[Pasted image 20230304220141.png]]

1. *Requirements specification*:  Son los requerimientos iniciales del sistema. No tiene que ser muy detallados pero debe tener los requerimientos esenciales esperables del sistema. 
2. *Software discovery and evaluation*: A partir de la etapa anterior de comienza a buscar sistemas y componentes, los cuales son evaluados para ver si son candidatos a satifacer los requerimientos, tambien se evalua el costo de los mismos (en caos que tenga un precio), y ademas si el mismo sigue siendo mantenido o no por quien lo desarrolo.
3. *Requirements refinement*: En base a los requerimientos iniciales, estos mismos son refinados a los componentes/sistemas encontrados. Si hay modificaciones que no son posibles, se debe volver a la etapa inicial. 
4. *Aplication system configuration*: Si se encuentra un sistema que cumpla con los requerimientos, en mismo se configura para crear el nuevo sistema. 
5. *Component adaptation and integration:* Si no se encuentra un sistema, se modifica los componentes encontrados y los que sean necesarios para el sistema. Luego todos ellos son integrados en el sistema. 

Un gran problema con este tipo de modelos es la compañia que desarrola este software piede control ya que el software que estan re-utilizando esta bajo el control de otra organziacion. 

Este modelo es frecuentement utilizado en los siguientes casos: 
- Stand-alone application. Ya que la mayoria de estos son se uso general, el cual se puede adaptar al cliente particular
- Collecion de objetos que son desarrolados como componentes o paquetes para ser integrados a un `component framework`.
- Servicios web que se desarrollan de acuerdo a estándares de servicio y que son
disponible para la invocación remota a través de Internet [ Traduccion textual, no tengo idea a que se refiere ]

A nivel de ventas:
- Se reduccen costos ya que no se desarrola de cero
- Se entrega el producto mas rapido
- Tiene por lo general mucho testing
A nivel de desventajas:
- Puede que el componente no tenga todos los requerimientos
- Perdemos control del componente encuando a su desarrolo futuro. 

## Process activities

> Real software processes are interleaved sequences of technical, collaborative, and managerial activities with the overall goal of specifying, designing, implementing, and testing a software system.

> The four basic process activities of specification, development, validation, and evolution are organized differently in different development processes. In the waterfall model, they are organized in sequence, whereas in incremental development they are interleaved

### Software specification

Es la etapa en la que se aplica *Rquirements enginnering*. Donde se entiende y define los reqerimientos del sistema y sus restriciones. 

Estos requerimientos por lo general son presentados en dos niveles de detalle: Uno para el usuario final (alto nivel) y otro para el programador (con mucho mas detalle)

![[Pasted image 20230304232340.png]]

- *Requierement elicitation and analiysis*: En este proceso se extran los requerimientos via observacion , discucion con clientes, analisis de tareas, etc. 
- *Requierement specification*: Se proceden a documentar los requerimientos encontrados en los dos niveles de detalles antes mencionados. 
- *Requirement validation*: Se validan los requerimientos documentados. Tanto su consistencia como completitud. 

Estas etapas estan entrelazadas, ya que encualquier punto de puede detectar un problema por el cual haya que ir hacia atras. 

### Software design and implementation
En esta etapa se hace el diseño y la implementacion del programa. 

El diseño de un software es una descripcion de la estructura a ser implementada, los modelos de datos, las interfaces ente los componentes, algunos algoritmos, etc. 

LAs actividades del diseño se realizan en simulatanio, y al mismo tiempo entra interelacionadas. 

Puede haber multiples insumos para el diseño, claramente uno son los requerimietos, pero tambien informacion de la plataforma donde el programa corre. 

Algunos ejemplos de actividades en el diseño son:
- Diseño de la arquitectura: Una generalizacion de la estructura del sistema y sus relaciones. 
- Diseño de la base de dato
- Diseño de la interfaces: interfaces entre componentes. La espesificacion de las interfaces debe ser no ambigua. 
- Seleccion de componentes y diseño de nuevos componentes. 

Por lo general la programacion y el diseño son actividades que estar intervaladas, pero hay veces que se requiere que el diseño este completo antes de comenzar con la programacion. 


### Software valitation
Se basa en la *verificacion* y *validacion* del sistema, de acuerdo a la espectativas del cliente. 

Hay 3 tipos de etapas en el testing:
1. *Component Testing*: Son pruebas unitarias de los componentes del sistema y son teteadas por los desarroladores. 
2. *System testing*: Aqui se prueba el sistema con todos sus componentes integrados, asegurandose que el sistema cumple todos los requerimientos funcionales y no funcionales solicitados. 
3. *Customer testing*: Ahora el sistema es probado por un cliente con informacion de prueba. De esta forma se puede asegurar que realmente el software cumple con los requerimietos reales de los clientes. 

En la metodologia agil las pruebas de tipo `Component testing` son definidas antes de comenzar con el desarrolo. 

Importante: La *verificacion* es probar que los requerimientos se cumplan o no. Mientras que la *validacion* es que el producto cumpla con las necesaidades del cliente, independientemente que cumpla con todos los requerimientos (no responde a la espesificacion). Osea que la validacion siempre presisamos la contrapartida del cliente 

El *V-Model* muestra que prueba de esta etapa valida cada etapa de el modelo de tipo cascada

![[Pasted image 20230305004716.png]]

### Software evolution
Aqui es una vez que software ha sido terminado, es como va a ir evolucionando. La mayoria de las veces uno se encuentra aqui, ya que es dificil que un software sea completamente nuevo. 
![[Pasted image 20230305005047.png]]


## Coping with change 

El cambio es una constante en el mundo del software. Y en el caso del software es mas facil hacer los cambios que por ejemplo en el mundo del hardware.

De todas formas los cambios generlamente involucran que partes del sistema que habian sido hechas deban ser rehechas (*rework*). 

Hay dos buenos encares para reducir los costos del `rework`: 
- *Change anticipation*:  Cuando en el software process se incluyen actividades para anticipar o predecir posibles cambios que podrian requerir rework. 
- *Change tolerance*: Que el software process este diseñado para que los cambios puedan ser facilmente hechos. 

Un par de ejemplos para estos encares podrian ser *System prototyping* y *Incremental delivery*. 

### Prototyping
Un prototipo es una version del sistema utilizada para demostrar conceptos, probar opciones y encontrar problemas y posibles soluciones. 

Un prototipo ayuda a poder anticipar cambios:
- Puede ayudar en la `requierement engineering process`, ayuda en la recoleccion de requerimientos y en la validacion de los mismos. 
- En el `design process` se puede utilizar para encontrar soluciones en el desarrolo, por ejemplo las interfaces de usuario. 
- Para el proceso de pruebas. Para ejecutar pruebas de "back to back":  Esto por ejemplo es utilizando cuando se esta sustituyendo un sistema antigo, se crean prototipos del sistema actual, y se compara el nuevo sistemas con el prototipo

En el siguiente digrama se resume el conjunto de etapas para desarrolar un prototiopo: 
![[Pasted image 20230305015619.png]]

Los primero es definir los objetivos del prototipo, y funcionalidades. Teniendo cuidado de cuales objetivos se dejan fuera del prototipo. 
Luego se procede con el desarrolo del mismo y por ultimo en base a los objetivos del prototipo se lo evalua en base al uso del usuario final. Hay que tener cuidado que al no ser el prototipo el producto final, puede ser que determinados funcionamientos hagas que el usuario se desvie de el objetivo del prototipo. Por ejemplo que al una funcionalidad ir muy lenta, deje de probarla. 

Bedeficios prototipado:
- Mejor usabilidad derl sistema
- Obtiene una mierda mas certera de las reales neceisdades del cliente
- Mejora la calidad del diseño
- Mejora la mantenibilidad
- Reduce el esfuerzo en retrabajo

**Importante**: Los prototiopos deben ser descartados si no confirman una buena base para el sistema en produccion

> La deuda tecnica es la deuda que uno adquirre de no desarrolar determinada parte del producto, y luego desarrolarla es mucho mas cargo que si se hubiera desarrolado desde un principio. [Def de la clase super informal]

### Incremental delivery
- Es un encare que se utiliza para liberar algunas versiones del producto al uso del cliente. 
- En caso de utilizar este mecanismo, esta bueno definir con el cliente que requerimientos tiene mas o menos importancia con el fin de priorisar estas liberaciones primero.  
- En la iteracion actual se tiene que tener los requerimientos definidos a detalle. No se aceptan nuevos requerimientos para la interacion actual, si para futuras. Osea cuando se desarrola lo pactado se libera y recien ahi se introducen al proceso de diseño (y los siguientes) los nuevos requerimientos. 

![[Pasted image 20230306193020.png]]

Algunas ventajas: 
- Pueden usar las primeras versiones como prototipos para irse familiarisando con el sistema. Y ademas no tiene que volver a aprender como funciona el sistema ya que estas funcionalidades son parte del sistema de verdad.
- Los clientes no tiene que esperar hasta la version final para realizar las acciones mas criticas.
- Es facil incorporar cambios en el sistema. 
- Las partes mas crusialies son las que reisven un testing mas intenso por ser las priemras en ser desplegadas, por lo que tienden menos a fallar. 

Alguas desventajas: 
- Es complicado la implementacion de estos sistemas cuando se esta construyendo un sistema que va a remplasar a otro. Los usuarios se niegan a usarlo por falta de funcionalidades. 
- A medida que va evolucionando el sistema, los distintos modulos utilizan un `core` con la funcionalidad comun. Si el core se va actualizando a medida que surgen los requerimientos, entonces la calidad del core se va degradando y eso es un problema porque impacta en todos los modulos. La idea es que el core sea desarrolado de priemra. Lo mejor seria definir ese core desde un inicio.
- Entra en conflicto con la forma de trabajar de muchas organizaciones. Las cuales por ejemplo antes de comenzar a trabajar en un proeyecto requieren saber todos los requerimientos. 

## Process improvement 

Hoy en dia se demanda mejor software, mas barato y mas rapido. 

*Importante*: La mejora de procesos significa entender los procesos existentes y cambiar dichos procesos para mejorar la *calidad del producto* y/o *reducir costos* y *tiempos de desarrolo*

En consecuencia hay dos enfoques acerca de la mejora de procesos:

- *Process maturity approach*: La idea es introducir buenas practicas de ingenieria de software. Sobre todo se enfocan en mejorar la calidad de los productos y la predicibilidad de los procesos. Eso introduce actividades que no tiene que ver directamente con el desarrolo. 
  Por lo que introduce costos (no solo economicos, sino en tiempo) que se podrian eliminar.
  Aqui es importante tener escritos los procesos a detalle. 
  
- *Agile approach*: Se enfoca en un estilo de desarrolo iterativo, para liberar rapidamente el producto. Se tiene por ejemplo a disminuir al minimo la documentacion

En el caso de el `Process maturity approach` la forma para iimplementarlo es mediante un proceso ciclico de la siguiente figura: 
![[Pasted image 20230305025120.png]]

Las etapas son: 
- *Process measurement*:  Se intenta medir via atributos la efectividad del proceso de mejora del software. Se esa forma se ve si el proceso va mejorando o no. Se piden los atributos que mas nos importa.
   Se deben recolectar datos *cualitativos* dentro de lo posible. Antes de tomar las medidas se debe tener escrito el proceso. Estas mediciones se usan para segurar la mejora del proceso. 
   Las medidas no deben guiar las mejoras, las medidas sirven de guia en base a los objetivos organizacionales. 
	Algunas ``metricas`` pueden ser:
		- Tiempo en completar el proces
		- Recursos requeridos 
		- Canrtidad de ocurrencias de un evento particular (EJ: cantidad de defectos descubiertos)

- *Process analysis*: Se analisa cuales son los problemas del proceso actual, y se lo documenta
- *Process change*: Se cambia el proceso en las cosas identificadas en el analisis. 

Se puede medir el nivel de madures del proceso via un sistema de 5 niveles Model ode capacidad de madures del SEIl).  
![[Pasted image 20230305025850.png]]

![[Pasted image 20230306214714.png]]
