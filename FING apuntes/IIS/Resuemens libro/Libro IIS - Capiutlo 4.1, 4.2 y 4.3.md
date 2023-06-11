
#### Dudas:
- [ ] Como que el nivel de espesificidad de un user requierement puede variar hasta ser una descripcion presisa?
- [ ] Ver bien la diferencia entre Requsitos no funcionaes de producto vs los Organizativos. Tratan de como se debe organizar el proyecto o porque provienene de la organizacion? 
- [ ] En la descripcion de `Requierement discovery and understanding` a que se refiere con que "and documentation are also discover during this activity"
- [ ] Ver bien la diferencia entre cliente y usuario (se dice en la clase pero no se entiende)
- [ ] Preguntar por el uso de los `Modelo de procesos` como obtencion de requerimientos. 
- [ ] Solucionar dudas marcadas en este documento

# Introduccion

- Los requerimientos de un sistema son una descripcion de lo servicios que el sistema deberia proveer y de las limitantes en sus operaciones. Los mismos reflejan las necesidades de un clinete en un sistema. 
- El proceso de encontrar, analisar, documentar y verificar estos servicios y limitantes se llama *Requirements engineering* (RE)
- Los requerimientos pueden tener dos formas las cuales sobre todo difieren en su nivel de detalle: 
	- `User requirements`: Se presentan en lenguaje natural y puede tener diagramas, expresa el servicio que se espera en el sistema y las limitaciones sobre la que opera. Puede variar su nivel de espesificidad. 
	- `System requirements`: Tiene una detallada descripcion de las funciones, servicios y limitaciones de operaciones. Debe definir con *exactitud* lo que va a ser implementado. Puede ser parte de un contrato entre el cliente y quien desarrola. 

 ![[Issimg1Cap3.png]]
 
- Estos tipos de requerimientos es elegido *segun a quien le vamos a comunicar el requerimiento*. El lector de los user requierements generlamente son personas que no estan involucradas en el desarrolo de la aplicacion ni les interesa los detalles. Por el otro lado quienes leen los System requeirements generalmente personas que deben conocer a detalle el sistema para ver su integracion con el bussiness process o porque estan involurados en la implementacion. 
	![[IssImg2Cap3.png]]
	
- "*System stakeholders* include anyone who is affected by the system in some way and so anyone who has a legitimate interest in it"
- Aunque generalmente La ingenieria en requisitos es presentada con el *la primera etapa del proyecto* en realidad puede haber una previa al proyecto en si para decidir si continuar o no con el desarrolo. Por ejemplo puede incluir un *estudio de factibilidad*. 
- La salida del proceso de RE se lo conoce como *requierements document*. Puede ser parte de un contrato. Por el contrario en la metodologias agiles se obtiene los requerimientos al mismo tiempo que se desarrola el sistema. 

#### Problema con los requisitos
- El mayor problema con los requerimientos es el *retrabajo* (rework), ya que alguna (o las dos) partes pierden. Algunos ejemplos cuando pasa esto podrian ser: 
	- Poco involucramiento de los usuarios
	- Planes inadecuados (por ejemplo crear planes a partir de requerimientos muy bagos)
	- Recorretes en los requerimientos de usuarios [DUDA: que es esto]
	- requisitos ambiguos
	- Agregar requerimienos que cremos que el usuario va a amar (*good plating*)
	- No identificar correctamente a los usuarios correctos (por ejemplo obtener requerimientos de usuarios que no son los adecuados)


# Requerimientos funcionales y no funcionales

- Como el titulo lo dice, los *system requirements* pueden ser clasificados en dos tipos: *Los requerimientos funcionales* y *los requerimientos no funcionales*. 
- La diferencia entre los dos no es tan facil de distinguir. 
- Los requerimientos generalmente no son independientes, algunos llevan a otros. 
- Estos requerimientos (los de sistema) no solo espesifica la funcionalidad que debe hacer el sistema, sino también especifican la funcionalidad necesaria para garantizar que estos servicios/características se entreguen de manera efectiva.

## Requerimientos funcionales
> Functional requirements These are statements of services the system should provide, how the system should react to particular inputs, and how the system should behave in particular situations. In some cases, the functional requirements may also explicitly state what the system should not do

- Los *requerimientos funcionales* describen que es lo que el sistema deberia hacer. 
- Estos requerimientos dependen del tipo de software a desarrolar, el usuario esperado y la estrategia de la organizacion.
- Los mismos pueden ser escritos como Users requierement o como System requierement. Cuando son escritos en la forma de estos ultimos se debe espesificar inputs, outputs y excepciones de detalle.  
- En algunos casos, no tiene sentido hablar de un requerimiento funcional, por ejemplo cuando el sistema a crear se basa en un sistema ya creado, y en ese caso lo que varia es la forma de mostrar y organizar la informacion. A estos tipos de requerimientos de los llama *information requirements*. 
- El no ser presiso con los  requerimientos puede llevar a disputas. Ya que un requerimiento funcional ambiguo puede llevar al desarrolador a implementarlo de una forma que a el le quede mas simple, pero no es lo que queria el cliente. 
- Los requerimientos deberian idealmente cumplir dos objetivos: 
	- *Completeness*: todo lo que quiere el cliente esta definido. 
	- *Consistency*: Cuando los requerimientos no son entre si contradictorios. 
- Generalmente solo se pueden conseguir ambos en sistemas muy pequeños. Generalmente se da por dos rasones: 
	- Es facil equivocarse cuando el sistema es grande 
	- Cuando hay muchos stakeholders con perspectivas y expectativas diferentes. 
- Los requsitos funcionales pueden ser escritos por ejemplo de dos formas: Que es lo que deberia hacer el programa (forma clasica) o que es lo que hace mi organizacion. Generalmente si quien escribe los requerimientos es la organizacion cliente, entonces los va a escribir de esta 2º forma, ya que sino puede pasar que los usuarios se temine adaptando al software, mas que el software adaptandose a los usuarios.


## Requerimientos no funcionales
> These are constraints on the services or functions offered by the system. They include timing constraints, constraints on the development process, and constraints imposed by standards. Non-functional requirements often apply to the system as a whole rather than individual system features or services.

- Estos requerimientos (como su nombre lo dice) no se enfocan que lo que debe hacer o no una funcionalidad/servicio para el usuario. Sino que *espesifican o limitan caraceteristicas que el sistema cumple como un todo*.  Osea trata de las propiedades y restricciones del sistema
- Generalmente son mas *criticos* que funcionalidades independientes. 
- A diferencia de los requerimientos funcionales, el no cumplir con los no funcionales puede llevar a que el sistema sea completamente inusable. 
- Por lo general los requerimientos funcionales se encuentran contenidos en una componente del sistema, mientras que los no funcionales se encuentran dispersos por todo el sistema, esto por lo general es por dos motivos: 
	- Afectan a la arquitectura del todo el sistema, en vez de componentes indivituales. 
	- Un solo requerimiento funcional puede generar multiples nuevos requerimientos funcionales relacionados, y tambien afectar algunos ya existentes.

#### Clasificacion de los requerimientos no funcionales
Hay 3 grandes categorias: 
- `Product requierements:` Espesifican o limitan el comportamiento del software en tiempo de ejecuccion. Algunos sub categorias podrian ser: 
	- `Performance requeirements`
	- `Reliability requierement`
	- `Security requierements`
	- `Usability requierements`
- `Organizational requierements`: "Estos requisitos son requisitos amplios del sistema derivados de políticas y procedimientos de las organizaciones del cliente y el desarrollador". Algunas subcategorias podrian ser: 
	- `Operational process requirements`
	- `Development process requirements`
	- `Environmental requirements`
- `External requierements`: Son los requerimientos que provienen de factores externos del sistema y de su desarrolo. Algunas subcategorias pueden ser 
	- `regulatory requirements`
	- `legislative requirements`
	- `ethical requirements`

![[IisImg3Cap3.png]]


#### Requerimientos no funcionales cuantitativo
- Un problema comun con los requerimientos no funcionales es que los stakeholders dan estos requerimientos de forma muy general. Por ejemplo "Que sea facil de usar", lo cual nuevamente deja libre de interpretacion. 
- Cuando es posible, los requerimientos no funcionales deberian ser escritos de forma cuantitativa, osea que pueda ser medible. De esa forma se puede testear si el sistema lo esta cumpliendo. 
- Generalmente los clientes no saben como expresar estos requerimientos de una forma medible. Y ademas tampoco entienden (o sea no creen que este justificado) generalmente el costo asociado a verificar que estos requerimientos se cumplen utilizando las medidas establesidad. 
- En la siguiente imagen se pueden ver algunos apartados que pueden ser requerimientos no funcionales con alguna forma de medirlos: 
	![[iisIm4Cap4.png]]
- Por lo general los requerimientos no funcionales estan relacionados con otros requerimientos no funcionales. 
 
> En la práctica, en el documento de requerimientos, resulta difícil separar los requerimientos funcionales de los no funcionales. Si los requerimientos no funcionales se expresan por separado de los requerimientos funcionales, las relaciones entre ambos serían difíciles de entender. No obstante, se deben destacar de manera explícita los requerimientos que están claramente relacionados con las propiedades emergentes del sistema, como el rendimiento o la fiabilidad. Esto se logra al ponerlos en una sección separada del documento de requerimientos o al distinguirlos, en alguna forma, de otros requerimientos del sistema.


# Otro tipo de requerimientos

No esta en el libro oficial. Mirar OF y el otro libro.

# Procesos en la ingenieria de requerimientos

- La *requirements engineering* incluye 3 actividades fundamentales: 
	- `Descubir los requerimientos`
	- `Espesificacion`: Convertir estos requerimientos ena forma estandar
	- `Verificar`: Verificar que los requerimientos realmente sea lo que el cliente quiere
	Esta primera etapa es el desarrolo de requisitos. Luego se entra en lo que se conoce como la *gestion de requisitos*. 
	![[Iiscap4Img5.png]]
	

- Estas 3 actividades se realizan de forma *incremental* e *intercalada*
- La salida de este proceso es un *system requierement document*.
- Al inicio del proceso, se invierte el mayor efuerso en entender en alto nivel el negocio del sistema, los requerimientos no funcionales y los  user requierements. Mas adelante (en los borden de la espiral, el enfoque esta los systems requierements y requerimientos no funcionales)
- El *modelo en espiral* se basa en ir evolucionando el desarrolo a medida que el nivel de detalle de los requerimientos aumenta (en las vueltas exteriores de la espiral). El numero de vueltas de la espiral puede variar, y se puede terminar cuando todos o algunos de los requerimientos han sido obtenidos.  
- Previo al proceso se puede hacer un *estudio de factibilidad*
	- Tiene como objetivo averiguar si vale la pena implementar el sistema, o si siquiera es posible con las restricciones actuales (calendario, prespuesto, tecnologia)
	- Como entrada tenemos algunos requisitos preliminaresa del negocio, brebe descripcion del sistema. 
	- Esto es muy util para ver cuando los sistemas son delicados

[Poner foto 4.6]

# Obtencion de requerimientos
- El objetivo de la *requierement elicitation* es entender el trabajo de los stakeholder y como podran utilizar el sistema para apoyar su trabajo. 

- Durante el proceso se busca obtener: 
	- Aplication domain ("An application domain is the segment of reality for which a software system is developed")
	- Work activities
	- Services and System features que quieren los Stakeholders
	- Performance requierements
	
- Este proceso puede ser dificil por los siguientes motivos: 
	- Los Stakeholder por lo general no saben lo que lo que quieren de un sistema. O no saben como expresarlo. O piden cosas inrealisas para un sistema en computacion.
	- Los stakeholder expresan los requerimientos en sus propios teminos, el cual puede implciar tener conocimiento de su trabajo. Si el ingeniero en requerimientos no tiene este conocimiento no va a entender el requerimiento. 
	- Diferentes stakeholder pueden expresar los requerimientos de forma diferente. Es el ingeniero el que debe encontrar los puntos en comun y contradicciones entre los mismos. 
	- Puede haber factores politicos los cuales hagan que algunos stakeholder pidan requerimientos para su propio beneficio en la organizacion.
	- Las condiciones de la organizacion puede cambiar, y por ende durante el proceso de obtencion de requerimientos, puede surgir nuevos requerimientos de por ejemplo nuevos stakeholder. 
- Un proceso de obtencion de requerimientos y analisis incremental puede ser el siguiente:
	[Figura 4.7]
- Las etapas son: 
	- `Requierement discovery and understanding`: Se interactua con los stakeholder para obtener los requerimientos. [Falta una parte]
	- `Requierement classification and organization`: Se agrupan los requerimientos relacionados. 
	- `Requierement prioritization and negotiation:` Se basa en priorizar los requerimientos y resolver los conflictos (debidio a que los mismos vienen de varios stakeholders ) via negociacion. 
	- `Requierement documentation:` Los requerimientos son documentados. Se puede ir adelantado una preview del software requierement document. O se los puede documentar informalmente. 

- Las primeras cosas que debemos intentar obtener a la hora definir cuales son las *fuentes de obtencion*. Algunas de estas son: 
	- Metas
	- Conocimientos de dominio
	- Stakeholders
	- Reglas de negocio 
	- Ambiente operacional = Como es el ambiente en el cual se opera 
	- Ambiente organizacional = Como son los procesos

- Este modelo general es adaptado segun la organizacion, tipo de sistema, experiencia de del personal, etc
- Una forma de agrupar es tomar todos los stakeholder de un grupo y considerarlos una *viewpoint*. Todos los requerimientos de ese grupo son de la viewpoint (Por ejemplo todas las cajeras) . Se puede aplicar lo mismo en los requerimientos de dominio y limitantes de otro sistema. Tambien se los puede organizar por los modulos del sistema a nivel de arquitectura. 

- Si un stakeholder no se siente que su punto de vista no fue considerado, entonces puede desestimar el proceso de obtencion de requerimientos. Osea *es importante mantener reuniones regulares con los stakeholders*

- Cuando se hace la Requirement documentation es importante que sea en un lenguaje simple con representacion con diagramas, asi los stakeholder puede ver el progreso. y hacer feedback. 

## Tecnicas de obtencion de requisitos

#### Entrevista
- Manera mas obvia 
- Usos: 
	- Entender el problema del negocio 
	- Entender el ambiente de operacion
	- Evitar omisiones de requisitos
	- Mejorar relacion con el cliente 
- Ventajas: 
	- Orientado a personas 
	- Flexible
	- Rico en cuanto contenido 
- Desventajas: 
	- Costoso en cuanto a tiempo
	- Depende de habilitades intrapersonales
- Tipos de entrevista: 
	- *Entrevista abierta:* Lista de preguntas determinada
	- *Entrevista cerrada:* Varios temas son explorados con el stakeholder. No hay un conjuto de preguntas predefinda. 
- Buenas estrategias para entrevistas efectivas: 
	- Tener mente abierta acerca de los requisitos
	- Utilizar preguntas como trampolin para generar discuciones. O trabajar juntos en un prototpio del sistema. 
	- Mantener el foco en la discucion en los objetivos 
- General mente es una mezcla entre entreviatas cerradas y abiertas
- Las entrevitas no son buenas para entender requisitos de dominio (osea los basicos)

#### Investigar antecedentes
- En esencia es googlear (Estuudio, muestreo, etc)
- Buena forma en comenzar un proyecto 
- Hay dos tipos
	- *Interna*: Estructura de la organizacion, procedimientos, informes, documentacion del sistema. 
	- *Externoa:* Publicacion de la industria y comercio, literatura, presentacion vendedores: 
- Ventajas: 
	- Ahorras tiempo de otros (clientes)
	- Prepara para otros enfoques 
	- Puede llevarse fuerza de la organizacion
- Desventajas: 
	- Prespectiva limitada = solo veo lo que otros hicieron
	- Desactualziado = vaya uno a saber cuando lo hicieron. 
	- Demaciaso generico = puedo perder el foco de lo que voy a hacer

#### Workshops
- Son reuniones estructuradas entre un grupo de shakeholder y expertos. Trabajan juntos para definir, crear, refinar y acortar documentos y modelos de los requerimientos de usuario. 
- Por lo general tenemos un facilitador el cual explica y mantiene la dinamica de trabajo
- Se recomienda tener grupos pequelos y tiempos fijos para cada tema
- Por lo general se los puede sacar del lugar de trabajo, y ademas la idea es que esten todos los stakeholders. 
- Ventajas: 
	- Muy efectivos para resolver conflictos entre stakeholders
- Desventajas: 
	- Costosos en tiempo y recursos

#### Focus grups
- Similar al anterior, pero no tengo a todos los stakeholders, lo que tengo son representantes de cada uno de los grupos de usuarios  que participan en el sistema. Osea solo trabajo con un grupo de persosnas para buscar requerimientos funcionales y de calidad de producto.  
- Nuevamente se requiere de un facilitador
- Ventajas: 
	- Utiles para explorar actitudes, preferencias y necesidadades de los usuarios
	- Son muy valiosos cuando no se puede tener acceso a todos los usuarios finales 
- Desventajas: 
	- Los resultados no son cuantitativos, es subjetiva. Se usara para evaluar y priorizar requisitos. 

####  Prototipado (En detalle)
- Las personas tiene dificutades para describir sus neceisdades sin tener nada tangible adelante. Mucho mas facil criticar que crear. 
- Nos da feedback temprano
- Nos permite compartir que es lo que entendemos de los requerimientos con los stakeholder. Disminuye el riesgo se insatifaccion
- Los usuarios prefieren un prototipo antes que tener que leer un documento de requerimientos. 
- Hay dos tipos segun el *alcance*: 
	- *Mock-ups:* 
		- Prototipo horizontales (Abarcan un aspecto, ej una GUI de usuario )
		- No realiza trabajo util, solo luce como si lo hiciera 
		- Muy utiles en interfaces de usuario
	- *Prueba de concepto:*
		- Prototipos verticales
		- Impelmentan una porcion funcional de la aplicacion
		- Permite resolver incertidumbres sobre que tan factible es la aquitectura, ya que funciona como el sistema real porque toca todos los niveles de la implementacion. Es muy buena para el apalear el *Riesgo tecnico*. 
- Segun el *Uso futuro*: 
	- *Desechables* 
		- Se hacen rapidamente para solucionar consultas, no elaborados. 
		- Cuidado con la calidad del producto al poner algo del prototipo desechable en la solucion final.
	- *Evolutivos*
		- Tiene una buena arquitectura para desarrolar el producto final en el mismo prototipo a medida que los requerimientos se van aclarando. 
		- Las metodologias agiles son un ejemplo de prototipado evolutivo. 
		- Debe ser construido cuidando la calidad y robustez del codigo
		- Son buenos para aplicaciones que crecen a lo largo del tiempo. 
- Segun la *Forma*
	- *Prototipos en papel*: 
		- Son de baja fidelidad.
		- La idea es de forma barata y rapida ver como va a lucir parte de un producto
		- La idea es explorar posibles alternativas de comportamiento y estetica del producto sin perderse mucho en los detalles. 
		- Interaccion rapida, util para refinar los requiermientos. 
	- *Prototipios electronicos*
		- Son de alta fidelidad 
		- Tiene una estetica muy similar a la que va a tener el sistema final. Sirve para clarificar requerimientos y estudiar comportamiento de usuarios. 

##### Validacion del prototipo 
- El prototipo debe ser evaluado en base a la usabilidad con el usuario. 
- Se aprende mas observando como trabajan los usuarios con  el prototipo. 
- Se deben validar con un publico objetivo
- Se pueden dar ciertas guias para su uso, pero evitar exagerar, asi vemos si usan bien o no el prototipo 

##### Riesgos
- Que el cliente crea que el producto esta pronto
- Que el cliente se enfoque demaciado en los detalles
- Generar expectativas inreales. 
- Invertir demasiado efuerso en los prototipos

##### Factores de exito
- Incluir estos prototipos en el plan de trabajo 
- Establecer los objetivos del prototipo primeros
- Planificar la construccion de varios de esto
- Crear protoiopos desechables tan rapido y barato como sea posible
- No incluir mucho detalles (ej validaciones)
- No prototipar requerimientos que no entiendo 
- Usar datos cercanos a la realidad 
- No remplazar los requerimientos por prototipos

##### Motivos para el uso de prototipos
- Aprender sobre tecnologias nuevas
- Medir el desmpeño de mi equipo ante una tecnologia
- Analizar riesgos tecnicos (Prueba tecnica)
- Aclarar, completa y validar reqeurimientos

#### Observaciones - Etnografias
- Implica observar a los usuarios mientras realizan las actividades
- Uno puede ser silencioso o interactuar con las personas
- Es util cuando los usuarios no saben como o no soy muy presisos describiendo su tarea. Tambien cuando esta tarea es compleja o dificil de explicar. O porque estan tan interiorisados ern la tarea que omiten detalles de forma inconsiente. 
- Ventajas: 
	- Es confiable porque soy yo quien releva
	- Una experiensa muy rica en cuanto a contenido 
	- Uno se integra en el equipo al pasar un tiempo, y resive una empatia por quienes releva. 
- Desventajas. 
	- Son muy caras 
	- Efecto Hawthorne: (derivado de la fisica cuantica) a quienes relevo debido a que los estoy observando cambian su forma de actuar. 
	- Hay que tener quidado de no generalizar a toda la organizacion basandome en grupo que observo 
	- Que a quienes observas no crean que sos un amigo indevido y que vas a cambiar los metodologias de trabajo de la organizacion. 
	- No tiene tiene a la inovacion 

#### Cuestionarios - Encuestas
- Son maneras de estudiar grandes grupos de usuarios. Bueno para validar y obtener datos estadisticos. 
- Para usar el enfoque se debe: 
	1. Determinar que informacion se busca
	2.  Determinar el enfoque mas adecuado: 
		- Abierto, cerrado o combinado
		- Multiple opcion, orden relativo, etc 
	3. Desarrolar el cuestionario
	4. Probarlo con perfil tipico
	5. Analisar resultados
- [Hay recomendaciones que no inclui ]
- Ventajas:
	- Ecnomica para la escala
	- Comoda de contestar
	- Puede ser anonima
- Desventajas: 
	- Menos rico en contenido 
	- La no-respuesta (no responder ciertas cosas) puede confundir a la hora de analizar los datos
	- Puede tener un efuerzo de desarrolo muy alto y la gente no contestar. 

#### Analisis de la interfaces del sistema
- Implica examinar los otros sistemas con los que se conectara nuetro sistema. Obtenemos  los requerimientos funcionales segun el intercambio de datos y servicios entre sistemas.
- Para cada sistema que se deba comunicarse con el nuestro, se identifican las funcionalides que nos pueden generar requisitos.  
- Util para las validaciones de datos que enviamos/resivimos de otros sistemas.

#### Analisis de la interface de usuario 
- Estudiar sistemas existentes para determinar requisitos de usuario y funcionales
- Se pueden ver una lista completa de las pantallas y nuevas potenciales caracteristicas. 
- Se puede utilizar pasos comunes de los usuarios. 
- Porque una funcionalidad este en un sistema viejo, no significa que sea necesaria y deba estar en el nuevo sistema. Lo mismo con el diseño de las pantallas. 

#### Analisis de documentacion
- Examinar la documentacion existente. Por ejemplo espesificacion de requisitos, manuales de usuario, etc. 
- No tengo que molestar a nadie mas que a mi. 
- Es una buena forma de introducirse a un nuevo dominio (osea usarlo antes de ir a una entrevista)

#### Tormentas de ideas 
- Se usa para ideas para "locas". Buena para la inovacion. 
- Ayuda a participar a todos los stakeholders
- Tiene dos fases: 
	- Fase generacion: Los stakeholders se reunen y se establacen objetivos. Cada uno escribe sus ideas. Sin jusgar, criticar o debatir
	- Fase de reduccion. Se len las ideas y se ve su viabilidad, se agrupan y por ultimo priorizan. 


#### Historias y escenarios 
- Las historias y escenarios describen como se puede utilizar el sistema para una tarea particular.  
- Describen que hacen las personas, la informacion que usan y producen, y que sistema utilizan. 
- Las historias se escriben con un texto narattivo que describe en alto nivel el uso del sistema. 
- Los esenarios NO son los mismo que la historia (mirar el libro)
- 

#### Casos de uso 
Ver el sigiente documento: [[Anexo Casos de uso]]

#### Historias de usuario 
- Son descripciones corta y de alto nivel de funcionalidades expresadas en termino de clientes. 
- Pueden teer la forma "As a ROLE, I want GOAL/DESIRE so that BENEFIT"
- La idea es que tenga la minima informacion necesaria para que se pueda estimar el efuerso de la implementacin. 
- La idea es no perder tiempo con los detalles de los requerimientos cuando posiblemente cambien. 

#### Modelado de procesos
- Permite enntender el trabajo con multiples pasos, roles y departamentos
- Los procesos complejos de descomponen para ayudar el entendimiento. 
![[IISCap4Img7.png]]

# Apuntes de la clase 
- Requerimiento != Requisito
- Reuqerimiento es una peticion por parte de los cliente
- Un requisito es la propiedad que debe tener el software desarrolado. 
- Osea las Necesidades + Requerimientos => Requisitos. Osea hay dos fuentes para los requisitos, niguna de las dos absulta. 

- Requisitos del sistema != Requisitos del software. 
- Los requisitos del sistema se pueden referisar a tenes de hardware, sofrware, sistema, etc. 
- Los requisitos tiene varios niveles y van nutriendo a los Software Requierements Specification. 
	![[iisCap4Img6.png]]
	 
- Niveles de requisitos no funcionales. 
- Clasificacion de sommerville
	- De producto
	- De proceso 
	- De organizacion
	- Externo
- Casificacion de Wiegers
	- Atributos de calidad = Tiene que ver con la calidad del producto (EJ: Confiabilidad, Escalabilidad)
	- Interfaces externas = El uso de una comunicacion de un sistema externo. Y el requisito es como es el uso con ese elemento externo. 
	- Restricciones: Todas las limitaciones que tenemos en el proceso (EJ plasos, lenguaje de desarrrolo)
- Los requerimientos no funcionales ttiene que ser verificables cuando se documentan.

## Proceso de ingenieria de requerimientos

## Tecnicas de obtencion

#### Etnografia
- Observar y participar 
- Diferencias la observacion segun los momentos (por ejemplo distinguir horas pico)
