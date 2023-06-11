
## Dudas 
- [ ] En las ventajas del equipo especializado se menciona que conocen mejor el modelo de negocio, ¿mejor que el equipo de desarroladores?

- En este cap se explica el rol del testing dentro del ciclo de vida de desarollo. Sea una el modelo en V como guia. 
- Cada ciclo de vida muestra una perspectivadel testing
- El modelo en V muestra que el testing es tan importante como el desarrolo. 

## Modelo en V
- La idea de este modelo es que el las actividades de desarrolo y testing tiene igual importancia. 
- La  rama isquierda muestra el proceso de desarrolo
- La rama derecha muestra el proceso de intergacion y testing. Este ultimo *finaliza* con las *pruebas de aceptacion*.
- El modelo en V es como el que sigue: [Añadir foto]
- Las partes son: 
	- **Requierement definition**: Las necesidades y requerimientos son recolectados, espesificados y aprobados. 
	- **Functional system design**: Se mapean los requerimientos con las funcionalidades 
	- **Technical system design**: Se diseña la implementacion del sistema. Ej interfaces, componentes (arquitectura.  
	- **Component specification**: De espesifica a detalle cada componente. 
	- **Programming**
	- **Component test**: Se verifica que cada componente cumple su espesificacion
	- **Integration test**: Se verifica que grupos de componentes interactuan de la forma que deberian 
	- **System test**: Se verifica que el sistema como un todo cumple con los requerimientos espesificados.
	- **Acceptance test**: Se verifica si el sistema cumple con los requisitos en el contrato y/o con las necesidades y expectativas del usuario.
- Por lo general *los fallos son encontrados* con los *test en el mismo nivel de abstracion*
- La *validacion* es el proceso de chequear que el resultado de desarrolo contra sus requisitos originales. Cuando se valida se jusga si el producto (parcial o completo) *soluciona la tarea y si cumple con el uso esperado*. Se *investiga* si el sistema tiene sentido en el contexto de uso esperado.
- La *verificacion* es el proceso de chequear que la salida de ese nivel de desarrolo haya sido obtenida correcta y completamente de acuerdo con el input de ese nivel de desarrolo. Aqui se verifica la correctitud y completitud de la fase, no si el producto es util en el contexto de uso.
- En el modelo en V, *no es verdad que el desarrolo comienza tarde* . El nivel de testeto del lado derecho corresponde a un nivel de execucion del testing, por ejemplo test planning y test analysis and design se puede hacer en paralelo al proceso de desarrolo. 
- La sepracion entre los niveles de testeo no es solo temporal, sino una sepracion tecnica, por lo que cada nivel requiere personal, conocimiento y objetivos diferentes.
- Como se comento, la *efectividad* de las pruebas es muy importante, pero tambien lo es el *orden*, ya que determinados datos de pruebas se pueden *reutilizar*. Eso es parte de las *planificacion* de las pruebas. 

#### Quien verifica?
- En la proximas secciones se dice por lo general *quien verifica cada nivel de prueba* . Pero la realidad es que *depende del proceso y del equipo*
- Tener un equipo especializdo (especialmente para las pruebas de sistema y aceptacion) tiene varias ventajas: 
	- Manejan mejor las tecnicas de prueba
	- Conocen los errores mas comunes realizados por los programadores 
	- Conocen el modelo de negocio (Hay empresas que se dedican a probar un negocio en particular, ej e-commers)
	- Se evitan problemas psicologicos en las pruebas, algunos por ejemplo
		- Los errores que el desarrolador comente a la hora de programar, generalmente los comete a la hora de probar
		- Debido a procesos inconcientes, tiene a hacer que las pruebas no hagan fallas el mismo 
		- Puede comprar mal el resultado esperado con el obtenido por un deseo que no falle el programa


## Component test

- Verifica el funcionamiento de los *componentes* de acuerdo s su *espesificacion* (ej contrato)
- *Normalmente* estas pruebas las hace el *equipo de desarrollo*. Generalmente el mismos que lo implemento. 
- Se requiere conocimiento detallado del modulo a probar, y por lo general no hay espesificacion 

- El *Objeto de prueba* son clases, modulos, scripts, etc. O sea es la unidad minima que es probable. 
- El *Entorno de prueba* es el entorno directamente el entorno del programador . O sea viene directaemnte del escritorio del programador. Por eso esta pruebas requieren un *alto nivel de cooperacion* con desarrollo
- El *Objetivo de prueba* es comporbar que la funcionalidad del objeto es *completa* y se desempeña y funciona adecuadamente de *acuerdo a su espesificacion*. Algunas cosas importantes de probar son: 
	- La *robustez* del componente (EJ añadiendo *test negativos*)
	- *Eficiencia* (uso de recursos)
	- *Mantenibilidad*

#### Estrategia de pruebas
- Hay dos tecnicas en general
- *Tecnicas estaticas*: Se basan en analizar el producto para deducir su correcta operacion. Un ejemplo de estas son las *reviciones*. 
- *Tecnicas dinamicas*: Ejecutan el componente para expermientar si el mismo se ejecuta cuando es esperado. Hay dos sub categorias:
	- *Testing Caja blanca*: Se basa la prueba en el codigo fuente del programa, el cual se utiliza para diseñar los casos de prueba
	- *Testing caja negra*: Basado en la espesificacion del programa
- Notar que la *verificacion* no son unicamente las pruebas, y ya que las *pruebas son dinamicas* y las *revisiones tambien son parte del testing.* 

#### Divers y Stubs
- Cuando tenemos que probar el modulo B de forma aisalada, hay que simplar quien llama al modulo (por ejemplo A) y a quien utiliza (por ejemplo E y F)
- Para simular las llamadas al modulo hay que usar un *driver*
- Generalmente los drivers son quienes dan los *casos de prueba* 
- Para simular los modulos de lo que el modulo B depende hay que usar *Stubs*.
- Los *Stubs* es una pieza de codigo que tiene los mismos parametros de salida y de entrada que el modulo faltante, pero con una simplificacion de comportamiento.
- Tiene un costo su realizacion
- Si el stub siempre debuelve los mismo valores de salida, entonces es posible que el modulo B no sea correctamente testado. 
- El *driver* es la pieza de codigo que *simula* el uso del modulo que sea esta testeado
- El *driver* es *menos costo* de realizar que un *stub*.


## Integration test
- Verifica que los grupos de componentes *interactuan* de la forma en la cual fue espesificada acorde al *diseño tecnico* del sistema.
- *Normalmente* es el equipo de desarrolo quien hace estas pruebas. 
- Es necesario tener conocimiento del diseño (interfaces y funciones en general)

- **Objeto de prueba**: El conjunto relacionado de las componentes
- **Entorno de prueba**:  EL entoirno de desarrolo, los drivers y stubs que ya fueron desarrolados en la prueba anterior
- **Objetivo de prueba**: Revelar problemas de interfaz, como de conflicto entre las componentes
	- Importante probar el intercambio de datos y la comunicacion

- **¿Podemos probar las pruebas de componente?**
	- Depende, el omitirlo va a aumentar la *dificultad de diagnostico*

#### Estrategia de pruebas
- Hay que determinar en que orden y forma hay que probar la integracion de los componentes
- La realidad es que los componentes van a estar disponibles en momentos diferentes
- El responsable de las pruebas de integracion debe elegir una estrategia que optimice:
	- Tiempo que insume
	- Costo del entorno de pruebas 
- Podemos tener estategrias de integracion *incrementales* y *no incrementales*
	- **No incrementales**
		- *Big bang*: Integro todo junto
	- **Incrementales**
		- *Bottom-up*: Integro los modulos de abajo de la jerarquia primero y voy subiendo. Requiero de muchos drivers.
		- *Top-Down*: Integro los modulos de abriba de la jerarquia primero y voy bajando. Requiero de muchos stubs
		- *Por disponibilidad (Ad hoc)*: A medida que los tengo
		- *Por integracion Backbone*: Primero se integra un core (o esqueleto), se los testea bien y luego se agrega el recto
		- Notar que en los 2 primeros se requiere que el sistema este estructurado de forma jerarquica
- Nuestro objetivo es combinar los modulos y componentes indivituales para que trabajen correctamente de forma conjunta. 
- Muchas veces se *combinan* las pruebas de componente e integracion, en la cual, (por ejemplo) si usamos un botton-up, podemos ir probando los componentes de abajo, y a medida se va subiendo en vez de usar stubs para probar las componentes de los cuales depende, podemos usar directamente el componente. En otras palabras, *podemos integrar junto con las pruebas de integracion para facilitar el proceso* , por ejemplo evitar generar stubs. 
- Esto ultimo aumenta (no mucho) la dificultad el diagnostico del problema, ya si ambas componentes estuvieras probadas, el problema seria solo posible en la integracion
- Para elegir una buena estrategia hay que tener encuenta ciertas cosas: 
	- *La Arquitecuta del sistema*: Cuales son las componentes y como se relacionan
	- *EL plan de proyecto*: Cuando durante el transcurso del proyecto las partes a probar deberian estar listas. Fundamental para defirir el orden. 
	- *El plan de pruebas*: Determina cuales aspectos del sistema deberian ser testeados, con cuanta intensidad y a que nivel. 
- Se puede hacer un mix de estas estrategias teniendo en cuenta aspectos como: 
	- Riesgo 
	- Disponibilidad
	- Costos
	- Otros...

## System test
- Determina si el sistema integrado (*como un todo*) cumple con los *requisitos espesificados*
- *Generalmente* es las realiza un equipo especializado (verificadores)
- Se requiere un conocimiento de los requisitos y una vision global

- El **Objeto de prueba**: El sistema integrado como un todo
- **Entorno de prueba**: Lo mas cercano posible al ambiente de produccion
- **Objetivos de prueba**: Validar que el sistema completo cumple con la especificacion de sus requisitos funcionales y no funcionales. Es imporntate: 
	- Verificar la documentacion y omision de requisitos
- No es imposible probar si no tenemos la documentacion o si la misma no es exacta, uno puede realizar *testing exploratorio* o aplicar de sus conocimientos en el dominio de la aplicacion. Pero eso no es siempre viable en todos los sistemas. 

## Prueba de aceptacion
- Verifica que el sistema cumple con los requisitos del cliente de acuerdo a como los mismos fueron *espesificados en el contrato* y/o el sistema cumple con las *necesidades* y *expectativas* del cliente
- Esta prueba se puede realizarse en niveles inferiores o distribuido en otros niveles. 
- Se requiere un conocimiento de los requisitos y una vision global

- **Objeto de prueba**: EL sistema (o parte) bajo la perspectiva del usuario/cliente 
- **Entorno de prueba**: El entorno de prod
- **Objetivo de prueba**: Validar que construimos el producto *correcto*
- **Bases de prueba**: Cualquier documento que describa el sistema desde el punto de vista del usuario/cliente: Ej CU, Procesos de negocio, user storys, etc.


#### Tipos de prueba de aceptacion: 
**Pruebas de aceptacion contractuales**

**Pruebas de aceptacion de usuario**

**Pruebas de aceptacion Operacionales**

**Pruebas de campo**
- Aqui tenemos las *alpha* y *beta* .
- Aqui tambien tenemos las *dogfood test*. Aqui los clientes que pruebas son el mismo equipo de desarrolo


## Nuevas versiones del sistema
- Luego que el software llegar por primera ves a prod, el mismo se puede ir actualizando y extendiendo con el paso del tiempo
- *Puede haber un deterioro* del software si se empieza a generar una deuda tecnica en los fix. Pero el software *no se gasta*
- El *mantenimiento* puede ser *correctivo*, *adaptativo* o *evolutivo*


### Prueba de regresion
- Soy necesarios en procesos iterativos incrementales. 
- Verifican que los cambios o agregados realizados no hayan degradado o roto el funcionamiento del sistema. 
- [Opcion] Verifican las funcionalidades previas al agregado del sistema, o sea los test viejos. 