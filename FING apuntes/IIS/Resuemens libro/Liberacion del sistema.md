- Comprende *todas* las *actividades* que son necesarias, luego que se ha construido y probado el software, para comenzar el uso del software. 
- *No* es unicamente desplegar el sistema
- Algunas de las actividades incluyen: 
	- Instalacion y configuracion
	- Adopcion (Tambien llamado conversion) del software. Esto refiere a *como va a ser la estrategia de liberacion*.
	- Entrenamiento y apoyo en el uso 
- Vamos a ver los 3. 

#### Instalacion y configuracion
- Instala el software de forma que quede disponible y operativo. Dependiendo del tipo de app, los pasos a seguir. 
- La *complejidad* depende de: 
	- *La tecnologia usada*
	- *Restriciones funcionales* (Eso puede incluir por ejemplo cuando debe estar liberado una nueva version)
	- *Requisitos de disponibilidad*. Haca hay aspectos como que versiones se encuentran liberadas simultaniamente para usuarios distintos, como tambien el grado de disponibilidad del software (ej 24 horas todos los dias el software debe estar disponible)
- La *facilidad* de la instalacion influye en la liberacion inicial y las siguientes durante el mantenimiento. 
- Algunas *actividades* que incluye son: 
	- Migrar o carga de datos iniciales
	- Parametrizacion de procesos = O sea, tener las configuraciones realizadas para el cliente en particular
	- Carga de usuarios y asignacion de permisos (o roles)
- La prueba final de esto es "Ver que todo anda". Pero eso no indica que una funcionalidad nueva este operando mal por un problema de una instalacion incorrecta. 

#### Adopcion (O conversion)
- Esto trata mas de "Como lo van a comenzar a usar". 
- Es la *definicion de la estrategia* de como mis usuarios lo van a comenzar a utilizar.
- Por lo general *ya se estaba utilizado otro sistema*. Por lo que se trata de un remplazo. 
- En el proceso de pasar de un sistema a otro se tiene que tener en cuenta: 
	- Si el pasaje va a ser *manual* o *automatico*
	- La *carga incial*
		- Esto incluye los datos basicos (tiene que ver con la instalacion)
		- La *informacion historica*, que son los datos que ya tengo del otro sistema. La *calidad de datos* depende de este item. 
- Inluye la *estrategia de conversion*. Aqui podemos encontrar 4:
	- *Big-bang*: En una fecha dada, todos los modulos son instaladores en la organizacion para todos los usuarios. 
	- *Paulatina*: Se libera de a poco. 
		- Se puede segmentar por: 
			- Modulo
			- Unidad de negocio 
			- Localizacion
		- Un *problema* es que se *convive con varios sistemas a la vez*
		- Un *beneficio* es que al ser menor la cantidad de usuarios, es *mas facil el ajuste de los prodecimientos*
		- Un lugar donde esta bueno usar esta metodologia es cuando en la version anterior hay un problema grabe, la cual se debe actualizar en todo el sistema, por lo que no puede ser paulatina. 
	- *Procesamientoen paralelo*: Tenemos un sistema en *produccion*, y otro para *prueba/control*
		- Muy util para *Entrenamiento* y para *validacion de la operacion*
	- *Estrategias hibridas*: Una comvinacion de las anteriores

- La *contigencia* define que hacer en caso que el *nuevo sistema falle*, o sea implida la operativa o tenga fallas importantes. 
- Algunas cosas que podemos hacer para evaluar la 


#### Entrenamiento y apoyo en el uso
- Tiene *4 actividades* 
	- **Entrenamiento para cubrir perfiles y necesidades**
		- Hay que definir cuales *grupos* hay que entrenar, hay dos:
			- *Usuarios finales*: Hay que decirles: *que hace el sistema* y *coomo usarlo*
			- *Administradores y operadores*: Estos por lo general son los que le dan asistancia a los usuarios finales. *Dar funciones de soporte* y debe saber *como funciona el sistema*  
		- Tenemos *diferentes necesidades* que hay que tener en cuenta a la hora de definir el entrenamiento
			- SI el usuario es *frecuente* o *eventual*
			- Que *nivel de rotatividad* de usuarios tengo (osea los nuevos usuarios). Capaz ahi me sirven mas los videos tutoriales.
			- Usuarios experimentados que necesitan *repasar*. O sea, se pueden hacer entrenamiento de repaso, segun la necesidad
			- *Entrnamiento especialidado*, por funcionalidades nuevas que requeiren una capacitacion aparte.
			
	- **Soporte para el entrenamiento**: Se pueden utilizar varias tacticas
		- *Documentos*
			- Hay que cuidar el tamaño, calidad y la relacion costo/beneficio
			- *Facilitan* el soporte y solucion de problemas
			- Su importancia depende de la cantidad y tipo de usuario objetivo (dispercion / diversidad)
			- *Atributos de calidad:* Legabilidad, Completitud (No tiene porque siempre serlo, hay veces que se hace manuales de algo puntual) y correctitud (siempre)
			- Para diferentes roles: 
				- *Manual de usuario*: Propocito general y funcionalidades
				- *Manual de operador*: Configuracion de hardware y software, solucion de problemas, acceso a usuarios, etc
				- *Guia general del sistema*: Se usa generalmente para que alguien compre el sistema, es corto. Tiene detalles que el cliente comprende, configuracion de hardware y software (asi ve compatibilidad) y la filosofia detras del sistema
				- *Guia para el desarrolador*: Muy util en la evolucion
		- *Ayuda en linea*
		- *Demostraciones* : Una demo del uso
		- *Talleres:* Junto con los usuarios y el equipo, practicamos de forma corta el uso
		- *Simulactros*: Ensayamos su uso como si estubieramos en la situacion
			- Estos 3 metodos son mas indivitualizados, o sea para situaciones especiales. Se *define* cuando se *realiza* segun el caso
		- *Usuarios expertos*: Enseñamos de gran manera a un usuario del grupo, para que el de ayuda de primer nivel
		
	- **Revision del entrenamiento**
		- Hay que *evaluar* el entrenamiento, algunas que se pueden hacer son: 
			- Ver el *grado de uso* del sistema (para ver cuanto se usa)
			- Ver que tan *eficientemente* lo utilizan
			- Ver el *cumplimiento de objetivos*
		- El entrenamiento *debe tomar en cuenta*
			- Caracteritcas y preferencas de a quien entrenamos
			- El estilo de trabajo de la organizacion o persona
			- Preciones de la organizacion (Ej los vagos del gremio no queiren hacer prueba)
			
	- **Apoyo durante el uso del sistema**
		- Hay veces que puede pasar que luego de haber terminado la capacitacion, se requiere ayuda extra
		- Algunas cosas que se pueden dar: 
			- Guia de mensajes de error
			- Guia rapida 
			- Mesa de ayuda (antes era Ayuda en linea)
				- Aqui podemos tener varios niveles: 1º, 2º, 3º , etc. Eso depende del grado de conocimiento que se requiere para ayudar al cliente.
			- Proceso de gestion de indicentes (se ve en la gestion de la configuracion)
			- Funcionalidades para deshacer (ctrl + z) y procedimientos de contingencia. 
		
