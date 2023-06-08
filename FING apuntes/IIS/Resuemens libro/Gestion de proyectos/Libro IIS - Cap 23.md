## Introducion
- El *proyect manager* debe:
	- Dividir tareas
	- Asignar tareas a los miembos del equipo
	- Anticipar problemas
	- Preparar soluciones tentativas a estos problemas
- El *Proyect plan* es creado al *inicio* del proyecto actualizado durante el mismo
- Hay 3 lugares donde aparece la *planeacion del proyecto* en el *ciclo de vida*:
	- *En la licitacion* (Proposal stage): ver si tenes los recursos y estimar el precio a dar al cliente
	- *Durante la face de inicio del proyecto*: Dividir el proyecto en incrementos , asignar recursos
	- *Periódicamente durante el proyecto*: Esta nueva información permite hacer mejores estimaciones de cuando va a llevar el proyecto. 
- Planear en el momento de la licitacion es inevitablemente especulativo. Debemos responder a un llado en base a una descripcion de muy alto nivel del problema
- En caso de ganar, hay que re planear el proyecto teniedo en cuenta la nueva informacion y cambios. 
- En la licitación *hay que dar un precio*. Para ello se debe *calcular el costo* del proyecto. Para ello se requiere calcular el *efuerso*. El calculo del costo debe ser *objetivo*. 
- A la hora de calcular el costo, hay 3 factores: 
	- *Costos por esfuerzo*: Pago a los desarrolladores (Este por lo general es el mas grande)
	- *Costos Hardware y software*
	- *Viajes y capacitación*
- Para el caso del costo por esfuerzo, hay que *añadir tiempo de contingencia* por si la estimación fue optimista.

- Una vez que se firmo el contrato, se debe realizar un *plan durante la fase de inicio de proyecto* se crea un plan para ayudar con cuestiones de *prespuesto* y *personal*. Nos sirve para saber si hay que contratar mas gente y como distribuyo los recursos. 
- También se definen *mecanismos de monitoreo*
- Los planes evolucionan en el transcurso del proyecto por cambios de requisitos, problemas de tecnología, etc. 
- El plan debe ser un *documento* que nos funcione para saber *que* debe ser hecho y para *cuando*. 
- En la *metodología agiles* también se hacen planes al inicio del proyecto. Solo que los mismos no debe ser detallados, solo debe tener la información básica. 

## Precio del software
- Para calcular el precio, *NO* es solamente costo + beneficio. Hay otros factores a tener en cuenta. 
- Por EJ hay que tener en cuenta cuestiones: 
	- **Organizacionales**
	- **Económicas**
	- **Políticas** 
	- **De negocio**
- Otros factores pueden ser: 
	- **Temas contractuales**: Por ejemplo que si el código lo podemos reutilizar el futuros proyectos. 
	- **Incertidumbre en los costos estimados**: Si hay mucha incertidumbre, puede aumentar los precios
	- **Salud financiera de la compañía desarrolladora de software**: Puede ser que baje los precios porque se esta fundiendo
	- **Oportunidad de mercado**: Capaz bajo el precio para meterme en un mercado nuevo. 
	- **Requisitos volátiles**: Si los requisitos son de cambiar mucho. Te bajo el precio del software y que cobro cada cambio. 
- Lo que se conoce como *Precio para ganar* (Pricing to win) Significa: La compañía tiene una idea de cual es el precio que el cliente espera y hace una oferta en base a ese precio esperado. 
- Luego que se gano el contrato, se *lleva a cabo un negociación* para acordar los detalles del sistema en base al precio acordado. 
- Este mecanismo* tiene la ventana para el cliente y los desarrolladores* que se eliminan los requisitos de difícil implementación para evitar costos mayores a los esperados. 
- Es posible dividir los costos del proyecto al hacerlo en *multiples versiones*

## Desarrollo por planes
- Se crea un *plan* que detalla a detalle: 
	- Que trabajo será hecho
	- Quien lo va a hacer
	- La agenda de desarrollo 
	- Los productos a desarrollar
- El plan se utiliza para *soportar la toma de decisiones* y *medir el progreso*
- El *problema* con el plan-driven es que *decisiones tempranas deben ser luego revisadas* debido a cambios. 
- Una *ventaja* es que potenciales problemas son descubiertos antes y tenerlas en cuenta. Por ejemplo temgas con otros proyectos o con los empleados. 
- Un proyecto debe ser un balance de ambas, dependiendo este balance del tipo de aplicacion a desarrolar. 
- En un plan-driven un plan debe incluir: 
	- Los recursos disponibles
	- Como se divide el proyecto
	- La agenda
	- El manejo de riesgo
	- Los riesgos detectados
- Generlamente los planes tiene las siguientes secciones: 
	- **Introducion** (objetivos y restricones)
	- **Organizacion del proyecto** (Como el equipo esta organizado, las personas que lo componen y sus roles)
	- **Análisis de riesgos**
	- **Requisitos de recursos de hardware y software**
	- **División del proyecto (WBS)**: Las actividades, las dependencias entre ellas
	- **Agenda del proyecto** (Cronograma)
	- **Mecanismos de monitoreo y reporte**
- Se puede añadir algunos planes extras, como los siguientes: 
	- *Plan de manejo de la configuracion*
	- *Plan de liberacion*
	- *Plan de mantenimiento*
	- *Plan de calidad*
	- *Plan de validacion*

- La *planeación de proyecto* comienza luego de creado el plan en la face de inicio del proyecto. Es un proceso incremental. 
- Este proceso se puede resumir en el siguiente diagrama: 
- ![[Pasted image 20230528221957.png]]
- Al principio del proyecto identificamos los *riesgos*, *restriciones*, y los *milestones* y *entregables*
- Los *Milestone* son puntos en los cuales comparamos la agenda definida con el progreso actual. 
- Los *entregables* son todos los productos que se entregan al cliente. 
- A partir de estos se define una *estimación de la agenda*, y las actividades identificadas son *comenzadas y/o aprobadas* 
- Luego de un tiempo se tiene que *monitorear* el progreso del plan, en búsqueda de discrepancias con lo buscado
- Cuando se define un plan, lo que se asuma, se debe hacer de forma *pesimista* para tomar en cuenta problemas inesperados. 
- En caso de haber problemas, hay que ejecutar los planes para el riesgo y re planear. 
- Re planear conlleva una negociación con el cliente
- Si el plan de contingencia no es efectivo, o la negociación con el cliente tampoco, hay que pasar a los *formal project technical review*. 
- El objetivo de las *formal project technical review* son buscar alternativas para continuar con el proyecto. 
- Esto puede levar a la cancelación del proyecto. 

## Proceso de la planificacion
- Este sigue las siguientes etapas: 
- ![[Pasted image 20230529162954.png]]
- El *Alcance* es definir que esta dentro y que no esta dentro de mi proyecto. Definiendo los entregables. 
- Luego se identifican las actividades y las dependencias
- Cuando hablamos de *estimar* es estimar tiempo en llas actividades que ya se identificaron.
- Luego se asignar los recursos
- Y por ultimo se crea el cronograma, lo que puede implicar cambios en la estimacion

#### Alcance
- Hay dos tipos de alcances:
	- **Alcance de producto**: Son las caracteristicas y funciones que describen un producto, servicio o resultado. 
	- **Alcance de proyecto**: Es el trabajo que hay que realizar para entregar el producto, servicio o resultado con las caracteiticas espesificadas. Notar que esto puede ir mas haya del alcance del producto, ya que por ejemplo aqui tenemos tenas de mesa de ayuda, o documentacion. 
- Es *fundamental* en el *alcance* decir que esta dentro y que esta por fuera del proyecto. 
- Una serie de pasos a realizar son: 
	1. Recopiar los requisitos
	2. Definir el alcance (que se incluye y que no)
	3. Crear un WBS o EDT
- La *ETC* o *WBS* es una descomposicion herarquina del *alcance total del trabajo* a realizar por el equipo del proyecto para cumplir con los *objetivos del proyecto* y crear los entregables
- Para crear una EDT hay que subidirir los entregables del proycto y el trabajo en componentes mas pequeños, hasta llegar a los *paquetes de trabajo*. A estos componentes se los tiene que *identificar*
- Una ETC tiene una visión estructurada
- Un *paquete de trabajo* es el trabajo definido en el nivel mas bajo, para el cual se puede *estimar, gestionar el costo y duración*. En otras palabras voy dividiendo hasta tener algo lo cual sepa como manejar. 
- Algunas características son: 
	- Los componentes de nivel inferior son necesarios y suficientes para el padre
	- *Regla del 100%*: El total del trabajo a los niveles inferiores corresponde al acumulado para los niveles superiores. De esta forma con los niveles inferiores no se omite ni hay trabajo extra
	- Descomponer nos permite *mejorar la capacidad de planificar, gestionar y controlar*. Pero *tiene costo*. 
- Algunas de las cosas que tiene que tener:
	- FOrma:
		- Nodos no pueden tener un solo hijo
		- [FALTA MIRAR PPT de la clase del martes]
- La idea es que cuando tengo un *paquete de trabajo*, se divida en *actividades* para realizar dicho ejecutable, esas actividades son luego las que conforman el cronograma. Por ejemplo si voy a hacer un workshop, tengo que tener una para reservar el lugar, otra para seleccionar a la gente, etc 
- Para el caso del software hay dos tipos de representación:
	- 1º representación: El 2º nivel tiene los entregabas principales
	- 1º representación: En el 2º nivel tenemos las fases del ciclo de vida.

## Estimaciones
- Es *predecir* la *duracion* y *costo* del proyecto. 
- Por lo general no son exactas por:
	- La espesificacion de requisitos no es precisa
	- El entorno es desconocido o la tecnología de punta
	- Experiencia del equipo
- A medida que el tiempo pasa, la incertidumbre disminuye notoriamente. 
- Una *estimación* es una *proyección* de la experiencia del *pasado* hacia el futuro, ajustando las diferencias entre el pasado y el futuro. Es por eso que es necesario: 
	- contar con experiencia del pasado
	- Saber algo del futuro
	- Es necesario saber como ajustar. Como el proyecto es único, hay que hacer determinados ajustes.
- Todas las estimaciones se basan en *supuestos* y *restricciones*
- Los proyectos requieren *re-estimarse* de forma periódica y aperiódica (en momentos particulares )

### Factores que influyen en la estimación
- **Tamaño**: Mientras mas grande es el software, mas líneas de comunicación hay, la productividad no es proporcional. 
- **Tipo de software**
- **Factores del personal**
- **Lenguaje de programación**: Depende de la experiencia y soporte del lenguaje de programacion

### Metricas del tamaño
- Como se dijo el tamaño juega un papel clave en la estimación, por lo que es de interés medirlo. 
- Es de interés porque es una de las formas mas objetivas dentro de los atributos.
- Este dato se puede "guardar" si ser usado como base de conocimiento para otros proyectos. 
- Hay dos tecnicas para las metricas de tamaño: 
	- **Por lineas de codigo**
		- Algunos problemas: 
			- Complicado estimar muy temprano en el proyecto
			- No es una buena idea medir la productividad de las personas por LOCs. Por lo general esa medida se hace a nivel de equipo
			- Hay que definir criterios claros de como contar
			- Puede variar demasiado de una persona a otra
			- La reutilizacion de componentes complejiza la relacion entre las LOCs (lineas de codigo) y los temas funcionales. 
	- **Por puntos de funcion**
		- Se cuenta la cantidad de entradas, salidas, archivos internos, queries e interfaces
		- A partir de los puntos de funcion encontrado se conviere a LOCs
		- Ventajas
			- Se puede medir sin tener codigo, solo con los requisitos
			- Es independiente al lenguaje
		- Desventajas
			- No es bueno para medir aplicaciones con mucho peso algoritimico
			- Medir Puntos de funcion es una tarea compleja

### Tecnicas para medir estimaciones
Hay dos tecnicas: 

#### Basadas experiencia
- La estimacion es realizada en base al conocimiento del equipo en proyectos pasados
- Algunas de estas son: 

##### Analogía
- Es encontrar proyectos analogos para utilizarlos como referencia
- Mientras mas similar mejor
- Podemos tener tablas con los proyectos pasados, e identificar similitudes entre ellos basados en cosas como:
	- Tipos de prodcuto
	- Tamaño
	- Duración estiminada / real
	- Factores de ajuste (Complejidad, experiencia del equipo de desarrolo)

##### Juicio de experto
- Se consulta con carios expertos para hacer la estimación
- Aqui generalmente vemos el caso optimista, el pesimista y el mas probable
- Una *ventaja* es que se tiene opciones diversidad y con criterio humano 
- Algunas *debilidades* son que los expertos pueden ser muy optimistas o se basen en experiencias incorrectas. 

##### Delphi
- Tambien tenemos expertos como en el anterior
- Solo que ahora tenemos etapas, en cada etapa los expertos estiman, y reciben antes toda la información de etapas anteriores, pero siendo anónima. 
- Por lo general *converge* , cuando no es asi se hace una reuion para ver diferencias. Si aun asi no se converge, se utilizan rango y probabilidad. 
- Algunas variantes de son: 
	- **Wideband Delphi**: Aqui tenemos una reunion de inicio, donde se discute el proyecto antes de comenzar con el proceso de Delphi puro. Notar que puede haber influencia en esta tecnica. 
	- **Planning poker** 

#### Algoritmos
- Se esta usando modelos matemáticos y atributos del producto
- Por lo  general la formula es de la forma: $A.Size^{B}.M$
- Donde: 
	- A = facor costante de la organizacion
	- Size = medica del producto
	- B = Complejidad (entre 1 y 1.5)
	- M = Factor que considera el proceso, atributos, etc 
- Tiene problemas
	- Dificil de aplicar en etapas tempranas
	- B y M son muy subjetivas
	- COmplejos y de difiicl uso.
	- Requieren que la organizacion las calibre, y muchas no tiene los datos historicos para hacerlo.
- Se usan por lo general 3 valores: El Peor caso, mejor caso y mas probable

##### Cocomo


## Desarrollo de cronograma
- Se crea un grafo de precedencias, donde se define el *camino critico*
- El *camino critico*, es el camino que si se retrasa retrasa todo el proyecto
- Puede haber mas de un camino critico 
- Puede cambiar durante el ciclo de vida 
- Para cada actividad se define: 
	- *Comienzo temprano (ES):* Lo antes que puede comenzar la actividad respetando precedencias y duraciones
	- *Fin temprano (EF)*: Fecha en la que finalia la actividad si comienza lo antes posible
	- *Comienzo tardío (LS)*: La fecha mas tarde en la que puede comenzar la actividad sin que afecte a la duracion del proyecto
	- *Fin tardío (FT)*: Lo mas terminar la actividad sin afectar la duracion del proyecto
	- *Holgura total*: Cuando puedo retrasar el comienzo de una actividad sin afectar la duracion total del proyecto
	- *Holgura libre:* Cuando puedo retrasar el inicio de un proyecto sin retrasar el inicio de ninguna de las actividades siguientes
- El camino critico son las actividades que tiene holgura total = 0
- El metodo para el camino critico es el mismo dado en IIO para el tema de ordenamiento de tareas
- La nomenclatura es: 
	- ![[Pasted image 20230529213546.png]]
- Una vez que tenemos el grafo, y sabemos cual es el camino critico, podemos armar el cronograma. 
- Cuando queremos llevar el grafo a un calendario, nos damos cuenta que no tenemos los recursos para determinados momentos. Es por eso que hacemos *una nivelación de recursos*
- Cuando aplicamos la nivelación de recursos:
	- Modificamos la fecha de inicio y fin del proyecto
	- Utilizamos esto cuando los recursos son:
		- Compartidos o criticos en momentos dados
		- Tenemos recursos limitados
		- Cuando queremos utilizar los recursos con un nivel constante de ocupación, o sea no déjalos ociosos ni muy cargados de a momentos
	- Eso cambia el tiempo del proyecto. También puede cambiar la composición del camino critico
- Cuando teneos que *comprmir* el cronograma, hay dos tecnicas: 
	- **Crashing**
		- La idea es acortar el cronograma con el menor incremento de costo posible
		- Por ejemplo: conseguir mas recursos, horas extras, etc
		- Solo funciona para actividades del camino critico
		- Ojo con aplicarlo siempre, no es recomendable ya que puede aumentar los riesgos y desgate en el equipo
	- **Fast tracking**
		- Actividades que se suelen hacer secuenciales se hacen en paralelo
		- Solo valido si las tareas se pueden paralelizar
		- Aumenta el riesgo y posible re trabajo