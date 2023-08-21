# Riesgos
- "Un *riesgo* es un evento o condicion *incierta* que si se produce, tiene un efecto *positivo* o *negativo* sobre al menos un *objetivo* del proyecto." 
- Dependiendo de la organizacion, como se va a tratar el riesgo
	- Las organizaciones tiene diferente *grado de tolerencia* al riesgo. Por ejemplo las organizaciones chicas no tiene una capacidad economica para poder soportar cualquier impacto economio.
	- La *actividad al riesgo* define la forma de responder
	- Ademas los riesgos se pueden *aceptar* o *rechasar* segun el *costo* y el *grado de recomenza/daño* que poseen
- Los riesgos pueden ser: 
	- **Riesgos positivos**: Oportunidad
	- **Riesgos negativos**: Amenza
	- **Riesgos negativos materializados**: Problemas

#### Categorizacion de riesgos:
- **De proyecto**: Afectan cronograma, recursos 
- **De producto**: Afectan calidad o performance del producto
- **De negocio**: Afectan el negocio relacionado al sistema desarrolado

## Gestion de riesgo
- Se gestionan los riesgos para no depender de la suerte. De forma tal de *mitigarlos* o *insentibarlo* (Me invente esta palabra)

### Proceso de gestion de riesgo
![[Pasted image 20230608190715.png]]
- Vamos a ver las etapas ahora
- 
#### Identificacion riesgos
- Determinar los riesgos y documentar sus caracteristicas
- Es recomendable buscar esos riesgos con *todo el equipo*
- Se tratan buscar riesgos de *alto impacto*
- Generalmente se utiliza una *checklist*
- Algunos tipos de riesgo:
	- De estimacion
	- De personas
	- Tecnologias
	- Heramientas
	- Requisitos
	- Organizacionales
#### Análisis riesgos
Hay dos tipos de *analisis*

##### Cualitativo 
- Subjetivo segun quien lo hace
- Para cada riesgo se determina: 
	- **Impato**: Medida del efecto negativo o positivo que causaria el evento en caso de ocurrir
	- **Probabilidad**: Que tan probable es que ocura el evento
	- **Severidad** = Impacto * Probabilidad
- Primero se gestionan aquellos que tiene una severidad mas elevada
- Dependiendo del grado de tolerancia, es a partir de que severidad los dejamos por fuera de la lista a gestionar. 

##### Cuantitativo
- Se analiza numericamente el efecto de los riesgos priorizados
- Ayuda a la toma de deciciones
- Aca por ejemplo se ven cuestiones numericas como el numero de dinero a invertir
- Pero tambien hay subjetividad


#### Planear riesgos
- Es desarrollar acciones para mejorar las oportunidades o reducir las amenazas
- Depende de la severidad la accion a tomar
- Estategias para riesgo negativo: 
	- **Evitar**: Cambiar el plan de elimiar, con el fin de *eliminar por completo* la amenaza. *Cambiar el objeivo* que esta amenzadado.
	- **Mitigar**: Reducir a un umbral aceptable la posibilidad y/o impacto de un evento
	- **Transferir**: Trasladar a un tercero todo o una parte del impacto negativo de una amenaza. (Ej contratar un seguro)
	- **Aceptar**: No cambiar el plan, aceptar el riesgo como es. Generalmente son aquellos que tiene una severidad mas baja que la tolerancia de mi organizacion
- Estrategia para riesgos positivos
	- **Explotar**: Eliminar la incertidumbre por completo, asegurando que la oportunidad se concrete
	- **Mejorar**: Aumentar la probabilidad y/o impacto de la oportunidad
	- **Compartir**: Asignar toda o parte de la oprtunidad a un tercero que este mejor capacitado para capturar la oportunidad en beneficio del proyecto
	- **Aceptar**: No cambiar el plan, tomar la ventaja si se presenta, tomando ventaja de ella, pero no se la busca de forma activa. 
- Los *planes de contingencia* son:
	- Aunque haya aplicacion acciones para intentar mitigar el riesgo, el mismo puede exitir luego, por lo tanto se usan estos planes. 
	- Son *Respuesta a riesgo*, que se utilizan si determinados eventos se producen
	- Se deben definir y monitorear los eventos que disparan los planes de contingencia
	- Se guardan recursos para le ejecucion de estos planes de contingencia. 

#### Monitorear riesgos
- Se hace un seguimiento periódico, en el cual se detectan:
	- Nuevos riesgos
	- Cambios en los riesgos
	- Riesgos que ahora son obsoletos
- Seguir las condiciones que disparan los planes de contingencia, con el fin de comenzar la ejecución de alguno. 
- Revisar como se están ejecutando la respuesta a los riesgos, y la efectividad de estas respuestas. 
- Modificar el plan


# Seguimiento

### Tecnicas de medicion
- Hay 3 formas de *medir el avance de una tarea*
	- **De formula fija (porcentaje fijo)**
		- Voy definiendo puntos en los cuales voy incrementando mi avance. Por ejemplo recien que supero el 50% considero que super el 50, pero en el resto del proyecto sigo en 50% y antes estaba en 0%.
		- Es ideal para tareas cortas
	- **Hitos con peso**
		- A los diferentes hitos les asignamos peso, por ejemplo los hitos pueden ser entregables
		- Sirve para tareas mas largas
	- **Porcentaje de completitud**
		- El responsable de la tarea estima el % completado
		- Tiene problemas con el *sincrome del 90%*

#### Enfoque del valor ganado
- Modelo en el cual todas actividades son unificadasa llevando a $ pos los costos planificados
- Se puede si se obtuno los costos y avance previsto
- Se puede obtener un % del avance, dia de atrasos, desciacion de costos, etc. 

##### Algunas definiciones
- **Valor planificado (PV)**: Lo que tendira que tener hecho hoy. Segun el valor que estime
- **Valor ganado (EV)**: Lo que tengo hasta ahora, segun el valor que estime en cada tarea
- **Costo actual (AC)**: Lo que llevo gastado para el trabajo hecho hasta ahora
- **Prespuesto planificado (BAC)**: ¿Cuanto prepuesto tengo pensando gastar?
- **Final planificado (FP)**: Fecha planificada de finalizacion del proyecto
- **Varianza de costos (CV)**: ¿Estamos por encima o debajo del prespuesto?
	- Formula: CV = EV - AC
- **Variacion de cronograma (SV)**: ¿Estamos adelantados o atrasados?
	- Formula SV = EV - PV
- **Costo performance index (CPI)** ¿Cuan eficiente estamos usando los recursos?
	- Formula CPI = EV / AV
	- Si es menor que uno, indica *sobrecosto*
- **Schedule performance index (SPI)**:¿Cuan eficiente estamos usando el tiempo?
	- Formula SPI = EV / PV
	- Menor que uno es atraso
- **Estimado a la Conclusión basada en costos (EAC)**
	- Formula EAC =  BAC / CPI
- **Estimado a la conslucion Basado en tiempo (EAC t)**
	- Formula EAC(t) = FP / SPI
	- ![[Pasted image 20230610220620.png]]
	- 