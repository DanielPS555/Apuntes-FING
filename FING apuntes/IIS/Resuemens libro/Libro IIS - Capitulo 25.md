
## Dudas
- [ ] Principio de inmutabilidad
- [ ] Cual es el beneficio de la integracion frecuente que no tiene la continua, pensando en las desventajas
- [ ] Preguntar a que se refiere con "metadata"  en la parte de configuracion
- [ ] Preguntar por la ppt de Alcance - Perspectiva
- [ ] 
# Introducion

- La *Confiuration management (CM)* estan enfocada en las politicas, procedimientos y herramientas para manejar el cambio de software del sistema. 
- Es necesario manejar la evolución del sistema porque es facil pedir vision de que cambios fueron incorporados en cada versión del sistema
- Las versiones  implementan propuestas de cambios, corrección de errores y adaptación de diferentes hardware y software. 
- **Objectivo**: 
	- Evitar el esfuerzo de modificar versiones incorrectas del sistema. 
	- Liberar versiones incorrectas del sistema
	- Perder la ubicacion donde se encuentra el software para una versión particular del sistema
- La CM es bueno para proyectos indivituales, es *esencial* para proyectos en equipos
- La CM involucra 4 actividades estrechamente relacionadas (Todas ellas se ven en detalle luego): 
	- **Gestión de versiones**
	- **Armado del sistema**
	- **Gestión del cambios**
	- **Gestión de liberación**
- CM utiliza una gran variedad de herramientas para: 
	- Almacenar versiones del sistema
	- Construir sistemas de los componentes 
	- Realizar el seguimiento de las liberaciones del sistema
	- Realizar seguimiento de las propuestas de cambio
- La 4 actividades del sistema se relacionan como muestra el siguiente grafico: 
![[Pasted image 20230612230802.png]]
- Con las *metodologías agiles*, cuando el sistema es múltiples veces cambiados por dia, es *imposible* de realizar sin el uso de CM tools. 
- El desarrolo de un producto software se desarrolla en 3 etapas diferentes: 
	- **Etapa de desarrolo**: 
		- El equipo de desarrollo es responsable de la configuración y nuevas funcionales añadidas
		- Son ellos quienes deciden que cambios deben ser hechos
	- **Etapa de testing**
		- Se realiza una liberación interna.
		- En esta etapa no se añade nuevas funcionalidades
		- Los cambios realizados son correciones de defectos y mejoras de performance o seguridad
	- **Etapa de liberación**
		- Se libera el software al cliente
		- Los clientes hacen *reportes de bug* y *propuestas de cambio*
		- Nuevas versiones atienden a esos apartados
- Para sistemas grandes, *nunca* hay una *sola versión del sistema*, siempre hay múltiples versiones en etapas diferentes del desarrollo. 
- *CM lleva el manejo de los componentes que son parte de cada versión del sistema*, y son incluidos como requeridos en la construcción del sistema. 
- Por lo general, CM es parte del *software quality management*. Es mas, el *quality manager* es responsable de: *quality management* y *configuration management*
- 
> When a pre-release version of the software is ready, the development team hands it over to the quality management team. The QM team checks that the system quality is acceptable. If so, it then becomes a controlled system, which means that all changes to the system have to be agreed on and recorded before they are implemented.


### Terminologia
- No hay un estándar en cuanto a la terminología
- Alguna de las terminologias mas comunes son: 
	- **Baseline**:  
		- Colección  de componentes que hacen a un sistema
		- Dada una baseline, la misma no puede cambiar
	- **Branching**
		- Se crea una nueva *codeline* desde una version existe de otra codeline
		- Se puede desarrolar independiente de las demas codelines
	- **Codeline**:  
		- Coleccion de versiones de un componente de software y otros items de configuracion
	- **Control de configuracion**
		- Proceso  que asegura que las versiones del  sistema y los componentes son guardados y mantenidos, de  forma que los cambios son manejados
		- Todas las versiones de los componentes y del sistema son identificadas y almacenadas durante la duracion del proyecto
	- **Configuration item**: 
		- Cualquier cosa asociada al proyecto que este bajo control de configuracion. 
		- Tiene un identificador unico
		- Segun la IEEE: 
		> Un agregado de hardware, software o ambos, que se ha diseñado para la gestion de la configuracion, y se trantan como una sola entidad en el proceso de gestion de la configuracion" 
		- En otras palabras, uno de estos items puede ser una clases desde una componente, siempre y cuando se los trate como una sola entidad 
	- **Mainline**
		- La secuencia baselines que representan las diferentes versiones del sistema
	- **Merging**
		- Creación de una versión de los componentes via la combinación de diferentes versiones de codeline. 
	- **Release**
		- Version del sistema que ha sido liberado a los clientes
	- **Repository**
		- Una base de datos compartida con las versiones de los componentes y información acerca de los cambios de estos componentes
	- **System building**
		- Es la creación de un ejecutable de una versión del sistema, vía compilando y vinculado todas las versiones de los componentes y librerías necesarias
	- **Version**
		- Una instancia de una archivo *configuration item* que difiere de alguna forma de otra instancia del mismo ítem
	- **Workspace**
		- Un area de trabajo privada, donde las modificaciones no afectan al resto de lso desarrolladores. 

- La gestión de la configuración se basa en el *principio de inmutabilidad* (Un ejemplo es que la información congelada no se puede modificar mas), esto implica la existencia de versiones y provee mecanismos y técnicas para que un equipo de personas pueda trabajar de forma coordinada. 

## Manejo de versiones
- **Definicion**
> Version management is the process of keeping track of different versions of software
	components and the systems in which these components are used. It also involves
	ensuring that changes made by different developers to these versions do not interfere
	with each other

- En otras palabras es el proceso de realizar *codelines* y *baselines*
- **Def (codeline)**
	- Secuencia de versiones de un codigo fuente, donde versiones posteiores se basan en las versiones anteriores
- **Def (baseline)**







Def (Ambiente): Es donde vive una instancia de mi sistema
Def(Promocio): Es cuando un producto es movido de un ambiente mas de desarrolo a uno mas de prduccion, o sea es que se va desplazando a la derecha.
Def(Debote) = Investo a Promocion 
Generalmente las promocion de pre-producion a produccion la da el cliente
