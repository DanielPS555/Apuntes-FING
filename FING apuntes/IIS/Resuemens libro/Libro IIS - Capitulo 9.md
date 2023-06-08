
# Dudas 
- [x] Calidad tecnica == Complejidad (en el inventario de pruebas)? => Invertidas
- [x] A que se refieren los dos ultimos puntos de la parte de Evaluacion de la aplicacion en la "Evaluacion de la calidad del sistema"
- [x] La refactorizacion === a mantenimiento perfectivo?? => MO

# Introducion
- Los grandes sistema de software tienden a tener una *larga vida*
- Los softwares deben *cambiar* si se quieren mantener usables
- Algunos de los factores que los pueden hacer cambiar son: 
	- Cambios en el negocio 
	- Cambios en la expectativa de los usuarios (nuevos requisitos)
	- Corregir errores
	- Adaptarlos por cambios en el hardware o en la plataforma de software
	- Mejorar algun atributo no funcional (EJ: Performance)
	- Lidiar con nuevas funcionalides de los competidores
- Por lo tanto los *motivos* por los cuales el software evoluciona:
	- Adaptarse al entorno operativo
	- Ádaptarse al usuario
	- Mejorar en el desempeño
	- Mejorar en funcionalidades
	- Correcion de errores
- En resumen: "El software debe *evolucionar* desde su liberacion inicial hasta que se retira del mercado"
- Se tiene que *invertir* para mantener valor en los software. Por lo general se gasta mas en evolucion que en otra cosa. Por lo general entre el 60% y el 90% del costo. Ademas un 75% del personal esta involucrado en actividades de evolucion. 
- Es incluso *mas caro* en sistemas empresariales, donde el sistema es parte de un *sistema de sistemas* . 
	- Se requiere examinar como un cambio *afecta al resto del sistema*. 
	- Se puede requerir que *otras partes* tambien deban evolucionar. 
- Hopkins and Jenkins llamaron *desarrolo de software brownfield* a situaciones donde el software debe ser *desarrolado y mantenido* en ambientes donde son dependientes de otros softwares.
- Debido por los cambios, *nuevas versiones* que incluyen estos cambios son *liberados* en de forma regular 
- A veces la necesidad de evolucion es evidente antes de terminar la version actual, por lo que *hay veces* que se *comienza con futuras liberaciones* *antes de terminar la actual*
- La *ingenieria en software* es entonces un proceso en espiral que dura toda la vida del proceso, como se muestra en la siguiente foto: 
	![[Pasted image 20230521225739.png]]
- Los *tiempos de cada ciclo* se han reducido significativamente, partiendo de 2 a 3 años, a un tiempo actual de semanas. 
- Cuando la *transicion* de desarrolo a evolucion *esta bien marcada*, se habla de **mantenimiento de software**
- El modelo anterior *es aplicable* cuando la compañia que hace el desarrolo y la encargada de la evolucion *es la misma*.
- En el anterior caso, la *metodologia y procesos* de desarrolo de software y la de evolucion es la misma.
- No siempre la empresa que hace el desarrolo es la misma que hace la evolucion. Hay veces que la empresa que cliente se hace cargo de la evolucion, hay otros casos donde la empresa cliente contrata otra empres que se haga cargo del desarrolo. Cosas locas...
- Cuando lo anterior pasa, el *pasaje de desarrolo y evolucion no es continuo*. Cuando se da esta discontinuidad, el *proceso de cambio del software post liberacion* se lo conoce como **software maintenance**. 
- *Software maintenance* incluye otras actividades mas haya de las de desarrolo de software, como por ejemplo *entendimiento del programa*. 
- Rajkuch y Bennett *propone una vision alternativa* del ciclo de vida del software en los sistemas empresariales. Como se muestra en la siguiente foto: 
- ![[Pasted image 20230521232018.png]]
- **Software evolution:** Face en la que cambios significativos son realizados a la arquitectura y funcionalidad. El software se encuentra en uso operacional y va evolucionando.
- **Software servicing:** Los unicos cambios realizados son los pequelos pero esenciales. Aqui el software sigue siendo util. No agregamos nuevas funcionalidades. 
- **Retiro gradual**: Se sigue utilizando el software, pero ya no se hacen mas cambios
- Notar que las dos anteriores etapas *se solapan*
- Al principio, cuando tenemos un software funcional, *muchos cambios son propuestos e implementados*, estando en la etapa de Software evolution. A medida que el software se va modificando, el mismo se va degradando, por lo que *hacer cambios se vuelve mas costoso* y  se comienza con la etapa de Software servicing. Aqui *los cambios que se hacen son pequeños y tacticos*. La compañia *esta pensando en como el software puede ser remplazado*. Al final es *retirado* de uso.  


# Proceso de evolucion
- *No* hay un *estandar para el cambio de software o evolucion*. 
- El metodo mas apropiado depende de: 
	- El tipo de software siendo desarrolado 
	- El proceso de desarrolo que utiliza la organiacion
	- Las habilidades de los miembros del equipo
- Las *propuestas de cambio* pueden ser *formales* (Ej en sistemas embebidos) o *informales* (Ej en sistemas para telefonos)
- Las *propuestas de cambio son el motor* para todo sistema de evolucion en toda organizacion.
- La propuestas de cambio traen una o varias *sugerencias de cambio*. Estas sugerencias pueden tener diversos origenes: 
	- Requisitos existentes que no fueron implementados
	- Nuevos requisitos
	- Bugs
	- Nuevas ideas de mejora del equipo de desarrollo. 
- El proceso de identificacion de cambio y evolucion del sistema es *ciclico* y dura durante todo el tiempo de vida del software. El ciclo de vida tiene 4 etapas en forma ciclica: 
	- Proceso de identificacion del cambio 
	- Propuesta de cambio
	- Proceso de evolucion del software
	- Nuevo sistema
- El *proceso de evolucion* del software se puede visualziar en la siguiente imagen: 
- ![[Pasted image 20230521211948.png]]
- Antes que una propuesta de cambio sea analizada, la misma debe ser *analizada* para ver *cuales componentes deben ser cambiados* y tambien sirven para *ver el impacto y costos* del cambio.
- **Importante**: 
	- No solamente hay que analizar que cambios hay que hacer en el software, sino en todo el sistema (procesos, V & V, etc), ya que un cambio en el software puede ser inofensivo, pero no en otras cosas.
	- Cuando el equipo de desarrolo y mantenimiento no son el mismo, entonces hay actividades de comprension del programa que se deben realizar en esta etapa
- Si el cambio fue aprobado, se debe realizar un *release planning* para *elegir cuales* de estos cambios se realizan y cuando. En el mismo todos los cambios propuestos son considerados. Algunos de los cambios propuestos pueden ser: *Fault repair*, *Platform adaptation* y *System enhancement* (Mejora del sistema).
- Una vez que se *decidio que cambios realizar*, los *cambios son implementados* y *verificados*.
- Por ultimo, una *nueva version del sistema es liberada*.

- En algunas situaciones, el proceso de desarrolo y de evolucion estan integrados. En ese caso el *change implementation* es simplemente *otra iteracion sobre el proceso de desarrolo*. 
- En el caso anterior, la *unica diferencia* es que en la evolucion, el feedback del cliente debe ser considerada. 
- En caso de *ser diferentes equipos*, hay una *diferencia critica*, la cual es que ante el primer *change implementation* se requiere *conocimiento del programa*. 
- Durante la etapa de *program understanding* los nuevos desarroladores deben: 
	- Entender como el programa esta estructurado
	- Que funcionalidad provee
	- Como los cambios propuestos pueden afectar el programa

#### Cambios urgentes
- *Todas las empresas* tiene algun proceso para los cambios
- En caso de un *cambio urgente*, se pueden omitir etapas del proceso del item anterior.
- La *politica del dia despues* dice que se tiene que anotar todas las cosas no hechas durante el dia de hoy (cosas que omitimos por ser un cambio urgente) para hacerlas el dia siguiente
- La *documentacion* de debe actualizar duante el proceso de evolucion. Tambien los *nuevos requisitos* deben ser *validados* y *analizados*.
- El hecho de realizar *prototipos* pueden facilitar la *estimacion* de *impactos y costos*
- Hay veces que surgen cambios de caracter **urgente**, en esos casos *la documentacion puede no ser actualizada*. Corriendo el peligro que si mas cambios urgentes ocurren, *el cambio sea olvidado* y la *documentacion quede no alineada con el codigo*
- Este es uno de los motivos para tener una *documentacion minima*. Un emblema de los *proceso agiles*
- Un *cambio urgente puede surgir* por varios motivos
	- Una *falla seria del sistema* fue detectada (afecta el funcionamiento normal) o *fallo de seguridad*
	- *Cambio en el ambiente del sistema* afecta la operativa habitual
	- Un *ambio no anticipado del negocio* (Ej nuevo competidor o nueva legislacion)
- Ante un cambio del sistema se busca una solucion *rapida y viable* antes que la *mejor solucion*, lo que *degrada el sistema*. Lo que afecta a la mantenibilidad del sistema. 
- *Idealmente* luego de la emergencia se debe hacer un *code refactor* para evitar degradacion

#### Metodologias agiles en evolucion
- Las *metodologias agiles* tambien *pueden ser utilizadas* para la evolucion. 
- Como los metodos agiles son incrementales, el pasaje de desarrolo a evolucion deberia seberia ser trivial
- El *test-driven* y *pruebas de regrecion automaticas* son utiles en la evolucion.
- El uso de *Scrum*, al estar enfocado en backlog, puede ayudar a priorizar los cambios. 
- La *involucrasion del cliente* tambien puede ayudar a priorizar. 
- Los cambios se pueden expresar en terminos de *historia de usuario*
- **La evolucion en metodologia agil, es simplemente continuar con el proceso de desarrolo agil**
- De todas formas, las metodologias agiles para desarrolo no son iguales que para evolucion: 
	- Es practicamente imposible involucrar al cliente cuando los cambios proviene de un amplio rango de stakeholders
	- Los ciclos de desarrolo se pueden ver interumpidos por reparaciones de emergencia
	- 

#### Pasaje de un equipo a otro
- Dos problemas pueden surgir durante el pasaje de un equipo de desarrolo a un equipo encargado de la evolucion: 
	- *El equipo de desarrolo* utilizaba una *metodologia agiles* , mientras que el equipo de evolucion utiliza *basado en planes*. Aqui falla que se *espera documentacion*. Posiblemente tampoco haya espesificacion de los requisitos del sistema
	- *El equipo de desarrolo* utiliza una *metodologia basada en planes*, pero el de evolucion utiliza una *metodologia agil*. Posiblemente falten *test automatizados*. El codigo posiblemente no haya sido *refactorizado y simplificado*, por lo que se puede requerir una *program reengineering*. 
- El concepto de *tranferencia* refiere al proceso de pasar de un equipo a otro (de desarrolo a mantenimiento, o de mantenimiento a mantenimiento)
- Generlamente puede haber reuniones entre el equipo que da y el equip oque resive, de forma que el equipo receptor solicita determinados apartados (ej documentacion)


## Sistemas heredados

- Son aquellos sistemas que son *viejos*, pero continuan siendo utilizado. Incluso pueden tener un *rol critico* en el negocio
- Algunas cosas a tener en cuenta
	- Pueden ser mas que software, tambien puede abarcar: Hardware, software, librerias, software de soporte, procesos de negocio
	- Han tenido un *mantenimiento por un largo tiempo*. Es posible que la *estructura este degradada*
	- Pueden tener dependencias con hardware antiguo
	- Pueden que *no soporten* *nuevos procesos de negocio*

#### Componentes de los sistemas heredados 

[Falta, buscar en el libro]

#### Dificultades y lo costoso del mantenimiento de los sistemas heredados
- Falta de habilidades y conocimientos de viejas tecnologias
- El codigo puede ser poco entendible por el numero de personas y estilos con el que fue modificado
- El sistema se pueden encontrar muy degraadado
- Puede tener vulnerabilidades de seguridad por nuevos tipos de ataques
- Problemas de integracion con tecnologias nuevas
- Ausencia de soporte oficial
- Puede usar hardware obsoleto que no se puede mantener o es muy costoso
- Problema a nivel de datos: Puede estar duplicados o tener baja calidad

#### Riesgos al remplazar un sistema heredado
Remplazar un sistema heredado puede implciar un gran riesgo, al mismo tiempo que un gran costo. Algunos aspectos a considerar son: 
- No existe espesificacion completa del sistema (no sabemos que hace)
- Los procesos de negocio seguramente tengas que ser modificados
- Reglas de negocio sean desconocidad porque estan "hardcodeadas" en el codigo sin documentacion
- Siempre desarrolar un nuevo software trae con sigo riesgos

#### Gestion de los sistemas heredados
Las organizaciones que los utilizan deben elegir la estrategia para evolucionarlos, algunas de ellas son: 
- *Desechar el sistema por completo* y modificar los procesos de negocios para presindir del programa
- Continuar el mantenimiento del sistema
- Tranformar el sistema por medio de la re ingenieria y mejorar la mantenibilidad. O sea, hacerlo de nuevo pero tomando el software viejo como correcto, y en el proceso garantizar que el nuevo sea mantenible. 
- Remplezar el sistema con un sistema nuevo. O sea, no sabemos si el software viejo "hace las cosas bien". Por ejemplo aca podemos aprobechar a cambiar incluso los procesos. 

Para tomar una decision de que hacemos, podemos usar el concepto de *Inventario de pruebas*. El cual habla de dos conceptos: *Criticidad* (Valor de negocio) y *complejidad* (Lo opuesto a Calidad sistema, si la complejidad es alta, es muy dificil modificarlo). 
Aqui podemos tomar las siguientes desiciones: 

- *Criticidad baja, Calidad de sistema baja*: Tirar
- *Criticidad alta, Calidad de sistema baja*: Se deben restructurar o remplazarse por otro sistema disponible
- *Criticidad baja, Calidad de sistema alta*: Estudiar porque es bajo. Se puede tomar cualquier accion: desechar o mantener dependiendo del resultado del estudio.
- *Criticidad alta, Calidad de sistema alta*: Continuar con el sistema en operacion, realizar un mantenimiento normal.

##### Evaluar el valor para el negocio (criticidad)
Para evaluar hay que tener en cuenta los puntos de vista de: 
- Usuarios finales del sistema
- Clientes del negocio (¿Diferencia con los anteriores?)
- Gerentes de linea
- Administradores

Para evaluar hay que tener en cuenta: 
- **Uso del sistema**: Los sistemas raramente usado, o poco usados tienden a tener un bajo valor
- **Que procesos de negocio son soportados**: Un sistema que fuerza el uso de procesos de negocio ineficientes, suelen tener un bajo valor de negocio
- **Confianza del sistema**: Los sistemas no confiables, que causan problemas a los clientes del negocio, tiene un bajo valor
- **Salidas del sistema**: Si el negocio donde se aplica el sistema, depende de las salidas del sistema, entonces tiene alto valor. 

##### Evaluar la calidad del sistema
Hay 3 aspectos a observar: 
- **Evaluacion del proceso de negocio**: La medida en que los procesos del negocio dan soporte a los objeticos actuales del negocio.
- **Evaluacion del entorno**: *Efectividad* del entorno del sistema y que tan *costoso* es su mantenimiento.
- **Evaluacion de la aplicacion**: Cual es la calidad de la aplicacion del sistema, Esti de oyede medir en 3 dimenciones: 
	- Cantidad de solicitudes de cambio
	- Numero de interfaces de usuario
	- Volmen de datos utilizados por el sistema


## Mantenimiento del software
- Se refiere a la *modificacion* de un programa, *luego* que este *este siendo utilizado*
- Generalmente el termino aplica a software *personalizado*
- Generalmente no hace grandes cambios en la *arquitectura*

#### Tipos de mantenimiento
- Una 1º clasificacion es: 
	- Mantenimiento para **reparar** *defectos* o *vulnerabilidades* del software. Dependiendo de en que etapa fue introducida, el costo de la correcion.
		- Se estima en un 24% 
	- Mantenimiento para **adaptar** del software a entornos operativos. El entorno *no tiene porque solo el entorno de software o hardware*, puede por ejemplo tan referir al pais donde se instalo
		- Se estima en un 19% 
	- Mantenimiento para *agregar* o *modificar* **funcionalidades**. O sea nuevos requisitos
		- Se estima en un 58% 
- Una 2º clasificacion (Pfleeger)
	- *Correctivo (21%)*: Reparrar fallas
	- *Adaptativo (25%)*: Adaptarse al cambios de entorno
	- *Perfectivo (50%)*: Mejorar funcionalidades existentes
	- *Preventivo (4%)*: Prevenir que el desempeño se degrade

#### Costo de mantenimiento
- Por lo general los costos son *mayores* que los de desarrolo
- El equipo de mantenimiento tiene que *entender* el problema
- Generalmente el equipo de desarrllo le falta *motivacion* para escribir software mantenible
- Por lo general el mantemiento *degrada* la estructura

#### Prediccion de mantenimiento
- Se encarga de evaluar *que partes* del sistema pueden causar problemas, y cuales seran los *costos de mantenimiento*
- La *aceptacion* de los cambios depende de la *capacidad de cambio* de los componentes afectados
- La *implementacion* de los cambios degrada el sistema y *disminuye* la *capacidad de mantenimiento*
- Los *costos de mantenimiento* depende del numero de cambio
- El *costo del cambio* depende de la *capacidad de cambio*
- Hay 3 dimenciones de la predicion de mantenimiento: 
![[Pasted image 20230523013941.png]]

##### Predicion del cambio
- Es predecir la *cantidad de cambios* requeridos, y comprender la *relacion* entre el sistema y su entorno. 
- Los sistemas muy *acoplados* con el entorno, requieren cambios cuando cambia el entorno
- Los factores que influencian esta relacion son: 
	- Cantidad y complejidad de las interfaces del sistema
	- Cantidad de requisitos que son volatiles de forma inherente
	- Los procesos de negocio donde el sistema se utiliza

##### Metricas de complejidad
- Para poder realizar prediccion de mantenimiento, puede ayudar *evaluar la complejidad* de los componentes del sistema.
- El mayor efuerso de mantenimiento se dedica a un numero pequeño de componentes
- La complejidad depende: 
	- Complejidad de estructuras de control
	- Complejidad de estructuras de datos
	- Objetos, metodos y tamaño de los modulos
- Eso depende mucho de la tecnologia utilizada

#### Metricas de proceso
- Utilizadas para *evaluar la mantenibilidad*. 
- Algunas metricas son: 
	- Cantidad de solicitudes de mantenimiento correctivo
	- Promedio de tiempo para el analisis
	- Promedio de tiempo para implementar cambio
	- Cantidad de solicitudes de cambio excepcional
- Un incremento en algunas de esto, nos puede indicar la perdida de mantenibilidad.

#### Algunos indicativos de necsidad de mantenimiento (clase del martes)
- 

## Reingenieria de software 
- Es la *reestructuracion* o la *reescritura* de una parte o todo un sistema heredad. *Sin cambiar la funcionalidad*
- Sirve cuando el *mantenibilidad es baja*
- Las *Ventajas* son: 
	- **Reducir el riesgo**: Siempre hay un gran riesto cuando el *sistema es nuevo*
	- **Reduccion de los costos**: Los costos de la reingenieria son menores que los de hacer nuevo software. 
- El proceso de la re-ingenieria se resumen aqui
![[Pasted image 20230523023041.png]]
- La reingenieria puede ser *automatica* (la que tiene menos codigos), o mas *manual* (en que se puede llegar a cambiar incluso la arquitectura)
- El *costo aumenta* mientras mas manual es.
- Algunos factores que determinan el costo son: 
	- La calidad del software a ser rediseñado
	- Heramientas disponibles
	- Grado de conversion de datos requerido (¿Quiero conservar los datos? ¿Como los puedo mirar a un nuevo esquema de la base de datos?) 
	- Disponibilidad del personal experto (un problema con los de la tecnologia vieja)

## Refactorizacion
- La *refactorizacion* es el proceso de realizar mejoras para *reducir* la *degradacion*
- Se lo puede ver como un *mantenimiento preventivo*
- Se modifica el programa para mejorar su mantenibilidad
- No se agrega funcionalidad
- En inherente a las *metodologias agiles*

## Refactorizacion vs reingenieria
- En la *reingenieria* el sistema previamente fue mantenido un tiempo, y los costos se han ido incrementando
- La *refactorizacion* es un proceso *continuo*, y se intenta evitar llegar al punto en que la mantenibilidad sea un problema.

## Bad smells
- Son señales que el codigo puede ser mejorado. O sea posibles puntos de mejora. 
- Algunos de ellos son: 
	- *Codigo duplicado o muy similar*
	- *Metodos demaciado largos*
	- *Sobre abusar del Swich*
		- Generalmente implica duplicacion
		- Se puede mejorar usando el polimorfismo en muchos casos
	- *Agomeracion de datos*: Cuando el mismo grupo de items de datos aparecen en varios lugares del programa
		- Se puede mejorar encapsulando estos elementos en un objeto
	- *Generalidad especulativa*: Incluye que se agrega generalidad a un programa por si en un futuro podria llegar a ser necesario, pero eso no ocurre. Al removerlo el codigo es mas simple. 
