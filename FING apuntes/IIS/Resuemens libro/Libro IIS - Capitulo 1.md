 
## Introduccion
- El software no esta limitado por propiedades fisicas, es por ello que puede crecer a puntos extremadamentes complejos, los cuales pueden ser muy dificiles de modificar. 
- No hay una notacion, metodo o tecnica universal para la ingenieria en software por los diferentes encares que pueden tener. 
- Hay algunos que afriman que la ingenieria en software es inedecuada en el software moderno.
- Por lo general hay dos motivos de fallo del software. 
		1. *Aumenta la complejidad de los sistemas*: La ingenieria en software ayuda a construir sistemas grandes y escalables. Hoy en dia los tiempos de entraga se han reducido, y es por eso que la ingenieria en software se debe adaptar. 
		2. *Una mala utilizacion del la ingenieria en software:*: un ejemplo claro es comensar un proyecto y sobre la marcha y usando estas tecnicas.  Muchas veces cuando no se usa correctamente, el software termina siendo mas caro y menos confiable



## Desarrolo profecional del software
- La principal distincion del software profecional es que esta hecho para ser usado por alguien mas que el desarrolador. Y ademas es desarrolado y mantenido por un equipo, no por individuos. 
- La intencion de la ingenieria en software es dar soporte al desarrolo de software profecional y no al individual. 
- Tiene tecnicas como: Espesificacion, diseño, verificacion, evolucion. Ninguna relevante para el desarrolo personal
- La ingenieria en software no incluye solo al programa, tambien contempla toda la documentacion, librerias, paginas de soporte, archivos de configuracion, etc. Generalmente es mas que un solo programa
- En el desarrolo profecional nos preocupamos en el hecho que personal que no desarrolador en programa lo van a usar, y otros ingenieros lo van a modificar. 
- Los ingenieros en software se preocupan en el desarrolo de software que se pueda vender a un cliente. 
- Hay dos tipos de productos de software: 
	1. ``Productos Genericos``: Son productos creados y son abiertos para que cualquiera pueda comprarlos. No son para un cliente en particular. Pueden ser para un tipo de cliente en particular, por ejemplo las biblotecas. 
	2. `Customized software`: Software que es diseñado para un cliente en particular. 

	La maxima distinicion entre ambos tipos de software es quien controla la espesificacion del software. Cuando es generico la compañia que lo desarrola es quien decide las espesificaciones, mientras que cuando es personalizado, es la compañia que paga quien decide. 
	Hoy en dia muchos software son diseñados genericos, y luego adaptados a casos particulares, por ejemplo SAP. Estos programas se los llaman Enterprise *Resource Planning (ERP) systems*.
- La *calidad del software* no depende unicamente de la funcionalidad. Ya que al ser cambiado por otras personas cosas como la documentacion o claridad del codigo son importantes. Aspectos como el comportamiento del programa tambien importan, no solo lo que el programa hace. Estas cosas se ven reflejadas en la calidad del software o en *atributos no funcionales*
- Algunos de estos atributos son: 
	- *Eficiencia*: Buena capacidad de respuesta, Buen uso de recursos, buenos tiempos de procesamiento. 
	- *Mantenibilidad*: Debe ser escrito para que el mismo pueda evolucionar con el paso del tiempo. 
	- *Aceptabilidad*: Tiene que estar diseñado para el tipo de usuarios finales 
	- *Confianza y seguirdad*: Incluye caracteristicas como la confiabilidad y seguridad del programa. No daños ante una falla del sistema, y protegido ante usuarios maliciosos. 


### Ingenieria en software 
Por definicion: *"Ingenieria en software es la disiplina ingenieril que se encarga de todos los ascpetos de la produccion de software, desde sus etapas de espesificacion hasta el mantenimiento luego que haya salido en uso"*

Dos aspectos importantes: 
- *Disiplina ingenieril*: Los ingenieros son los que aplican la teoria, heramientas en los lugares apropiedos. Usandolas selectivamente e inventando mecanismos cuando no hay un metodo o aplicacion clara. Al mismo tiempo se restrigen a limitaciones organizacionales y financieras. 
- *Todos los aspectos de la produccion de software*: No solo se procupa de los temas tecnicos del software, sino todos los aspectos (prohect managerment, methods y theories)

> In general, software engineers adopt a systematic and organized approach to their work, as this is often the most effective way to produce high-quality software. However, engineering is all about selecting the most appropriate method for a set of circumstances, so a more creative, less formal approach to development may be the right one for some kinds of software

#### Porque ingenieria en software es importante
Es por dos razones: 
- Los indivituso y sociedades confian en sistemas de software cada vez mas avanzados, que tiene que ser confiables, economicamente seguros y rapidos
- Es mas barato a la larga usar los metodos de ingenieria de software en vez de escribir un programa como un programa personal.


#### Software process 
El abordamiento sistematico se la ingenieria de sofware de los llamada *software process*, y es un conjunto de actividades, las mas comunes son las siguientes 4. 
- `Espesificacion de Software`: Espesificar lo que tiene que hacer el software y sus limitantes 
- `Desarrolo de software`: Donde se diseña y programa
- `Validacion de software`: Donde se chequea con el fin de validar los requerimientos
- `Evolucion del software`: Donde se lo modifica para adecualos a nuevos requerimientos

Estos pasos pueden variar dependiendo de el tipo de sistema. Por ejemplo hay sistemas donde se tiene todos los requerimientos antes de desarrolar el proceso. Mientras que en otro se va dando en paralelo. 
Para algunos proyectos se hace un analisis de factivilidad precio a la espesificacion de software. 

#### A quien esta relacionado la ingenieria en software
Tanto a los ingenieros en sistema, como a la 'Computer science'. 

- Los ingenieros en sistema se encargan mas de los temas practicos de la produccion de software. Mientras que la `Computer science` tiene mas enfoque en la teoria por debajo de la  computadora y sistemas operativos. 
- Los ingenieros en sistema se encargan del desarrolo de hardware, politica y procesos de diseño, sistema de liberacion como de la ingenieria en software. Osea *todo los aspectos del desarrolo y evolucion de sistemas complejos donde el software es el mayor jugador*

#### Problemas generales de los software
Estos problemas afectan a la gran mayoria de los tipos de software. 
- `Heterogeneidad`: Crear un sistema que pueda operar de forma distribuida y en multiples tipo de dispositivos diferentes (tablet, computadores, etc) de forma confiable. 
- ``Cambios sociales y de negocio``: Los cambios sociales, economicos y tecnologicos son muy rapidos. Se requiere de tecnicas para poder evolucionar el software en menos tiempo. 
- `Seguridad y confianza`: Los sistemas de software deben ser confiables para que las personas lo puedan usar en su dia a dia. Al mismo tiempo que se proteje de los usuarios maliciosos. 
- `Escaliabilidad`: El software a medida que es creado debe poder pasar por un gran conjunto de escalas. Desde una pequeña escala hasta sistemas gigantes.


### Diversidad de la ingenieria en software 

- No hay un metodo generico de ingenieria de software para cada tipo de software y de compañia. 
- La iniciativa SEMAT propone que hay un meta-proceso fundamental que puede ser utilizar para crear diferentes tipos de procesos. 

#### Tipos de aplicaciones 
1. `Stand-alone applications` (aplicaciones independientes): Aplicaciones que corren en una computadora personal y tiene todas las funciones necesarias. 
2. `Iteractive transaction-base applications` (Aplicaciones iterativas basadas en transaciones): Aplicaciones que se ejecutan en computadoras remotas accedias por usuarios desde sus maquinas. Ej: pagina web 
3. `Embedded control systems` (Sistemas de control integrado): Estos son los softwars que controlan los dispositivos de hardware. 
4. `Batch processing systems` (SIstemas de procesamiento por lotes): Son sistemas que estan pensados en processar grandes volumenes de informacion para crear salidas. EJ: Sistemas de facturacion.
5. `Entertainment systems` (SIstemas de entretenimiento): Sistemas personales utilizados para entretener al usuario. Por ejemplo juegos
6. `System for modeling and simulation` (Sistemas para modelado y simulacion): Son sistemas para modelar procesos o situaciones, con muchos objetos iteractuado y separados
7. `Data collection and analysis systems` (Sistemas de recoleccion de datos): Son sistemas que se encargan de recolectar informacion de su ambiente y enviarla a otros sistem para su posterior procesamiento. 
8. `System of system` (Sistemas de sistemas): Son sistemas que estan compuestos por otros sistemas. Generalmente utilizados en corporaciones de gran tamaño. OSea se comvinan los anteriores. 

Hay fundamentos que aplican a la ingenieria de software de todos estos tipos: 
- La organizacion de desarrolo del software debe tener un plan de desarrolo con ideas claras y con fechas de terminacion
- Garantizar la confianza y performance
- Entender los requerimientos y los tipos de clientes. Tambien manejar sus expectativas para que se pueda completar el sistema en tiempo y prespuesto.
- Hacer buen uso de los recursos. 

### Ingenieria de software de Internet
Con el invento de internet surgieron los navegadores, los cuales pueden correr pequeños programas, donde el software es desplegado en servidores remotos. Eso hizo mucho mas baratos los costos para actualizar el costo e instalacion. 
Esto cambio dramaticamente la forma en la que el negocio del software se organizaba. 

Algunos cambios radicales en la creacion de aplicacion web-base systems: 
- La reutilizacion se ha convertido en un factor determinante en la construcion de sistemas web-base. Osea se pienza como se puede reutilizar lo ya hecho. 
- No es practico espesificar todos los requerimientos por la facilidad de la actualizacion del sistema. 
- El software se puede implementar usando servidores, donde aplicaciones de tipo stand-alone corren como web service en servidores remotos


## Etica de la ingenieria de software 

Para la etica hay ciertos codigos de responsabilidad profecional que habia que seguir: 
- *Confidencialidad*: Resoetar la confindencialidad de tu empleado y clientes aunque no haya contrato
- *Comprencion*: No se debe aceptar concientemente trabajo que este fuera de tu comprencion 
- *Intellectual property rights*: Respectar las leyes que tratan las patantes y copyright
- *Mal uso de la computadora*: No usar tus conocimiento para hacer un mal uso de las computadoras de otros.

Tambien the ACM/IEEE diseñaron un codigo de etica, en su version corta es asi: 
![[Pasted image 20230304002241.png]]

Estos principios identifican la responsable y etica relaciones que los individuos y organizaciones participan y sus principales obligaciones dentro de estas relaciones. 

Aqui vemos que hay dilemas eticos, notar que hay situaciones borde donde estos propios principios se contradicen. Es por eso que en esos casos uno debe decidir segun su comprencion, las personas involucradas y el daño potencial, que decision tomar. 