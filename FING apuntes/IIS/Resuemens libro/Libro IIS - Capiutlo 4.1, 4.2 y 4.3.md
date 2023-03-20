
#### Dudas:
- [ ] Como que el nivel de espesificidad de un user requierement puede variar hasta ser una descripcion presisa?
- [ ] EN la descripcion de `Requierement discovery and understanding` a que se refiere con que "and documentation are also discover during this activity"

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
	- *Completeness*: Cuando toda la informacion y servicios requeridos por el usuario se relevan. 
	- *Consistency*: Cuando los requerimientos no son entre si contradictorios. 
- Generalmente solo se pueden conseguir ambos en sistemas muy pequeños. Generalmente se da por dos rasones: 
	- Es facil equivocarse cuando el sistema es grande 
	- Cuando hay muchos stakeholders con perspectivas y expectativas diferentes. 

## Requerimientos no funcionales
> These are constraints on the services or functions offered by the system. They include timing constraints, constraints on the development process, and constraints imposed by standards. Non-functional requirements often apply to the system as a whole rather than individual system features or services.

- Estos requerimientos (como su nombre lo dice) no se enfocan que lo que debe hacer o no una funcionalidad/servicio para el usuario. Sino que *espesifican o limitan caraceteristicas que el sistema cumple como un todo*. 
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


# Procesos en la ingenieria de requerimientos

- La *requirements engineering* incluye 3 actividades fundamentales: 
	- `Descubir los requerimientos`
	- `Espesificacion`: Convertir estos requerimientos ena forma estandar
	- `Verificar`: Verificar que los requerimientos realmente sea lo que el cliente quiere
- Estas 3 actividades se realizan de forma *incremental* e *intercalada*
- La salida de este proceso es un *system requierement document*.
- Al inicio del proceso, se invierte el mayor efuerso en entender en alto nivel el negocio del sistema, los requerimientos no funcionales y los  user requierements. Mas adelante (en los borden de la espiral, el enfoque esta los systems requierements y requerimientos no funcionales)
- El *modelo en espiral* se basa en ir evolucionando el desarrolo a medida que el nivel de detalle de los requerimientos aumenta (en las vueltas exteriores de la espiral). El numero de vueltas de la espiral puede variar, y se puede terminar cuando todos o algunos de los requerimientos han sido obtenidos.  

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

- Este modelo general es adaptado segun la organizacion, tipo de sistema, experiencia de del personal, etc
- Una forma de agrupar es tomar todos los stakeholder de un grupo y considerarlos una *viewport*. Todos los requerimientos de ese grupo son de la viewport. Se puede aplicar lo mismo en los requerimientos de dominio y limitantes de otro sistema. [DUDA]
- Si un stakeholder no se siente que su punto de vista no fue considerado, entonces puede desestimar el proceso de obtencion de requerimientos. Osea *es importante mantener reuniones regulares con los stakeholders*
- Cuando se hace la Requirement documentation es importante que sea en un lenguaje simple con representacion con diagramas, asi los stakeholder puede ver el progreso. y hacer feedback. 





