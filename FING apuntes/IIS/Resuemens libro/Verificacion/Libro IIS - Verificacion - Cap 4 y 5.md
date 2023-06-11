
## Dudas
- [ ] Se hace referencia a clases de equivalencia de la entrada y la salida. ¿Que diferencia hay? 
- [ ] Como puedo generar un caso que prueba varias clases de equivalencia valida si las entradas de una clase y otra son disjuntas?
- [ ] Expandir los criterios de cubrimiento condicion y decision/condicion
- [ ] Ver mejor las diferencia entre alpha y beta testing 
- [ ] "Su generalidad no es siempre clara (solo se aseguran los casos probados)"(Diapositiva 8, parte 4) ¿Y en estaticos si?

## Tipos genericos de pruebas 
Hay multiples tipos, dependiendo en que se basan y que prueban
- **Prueba funcional**: Verifica las entradas y salidas del sistema
		Se utiliza generalmente *caja negra* (basa en requisitos)
- **Prueba no funcional:** Se verifica en que grado se cumple los requisitos no funcionales. 
		Se utilizan las pruebas funcioanels para recrear el escenario donde se prueba la caracteristica
- **Prueba de la estructura del software:** Se basan en la estructura de los artefectos (codigos, requisito, arquitecutra)
		Las tecnicas de *caja blanca* (tambien llamadas como *tecnicas estructurales* )
- **Pruebas relacionadas a los cambios**: Son pruebas relacionadas a los cambios. Aqui tenemos las *Pruebas de regresion*. 
	Estos cambios pueden ser cualquiera de los otros 3

## Tecnicas de verificacion
- **Tecnica estatica**: Analizan el producto para deducir su correcta operacion 
	- Analisis de codigo
	- Analisis estatico (de codigo)
- **Tecnicas dinamicas** (Pruebas): Ejecutan el producto para ver si el comportamiento del producto es el esperado 
	- Caja blanca
	- Caja negra 
	- Basa en experiencia

### Tecnica estatica 
- **Analisis de codigo:** 
	- Se revisa el codigo buscando defectos
	- Se puede llevar acabo de grupos
	- Hay dos tecnicas principales: *recorridas* e *inspecciones*
	- Lo hacen personas
- **Analisis estatico:**
	- La entrada es el codigo fuente y la salida es una serie de defecto detectados
	- Es realizado por una heramienta, por ejemplo un compliador

#### Analisis de codigo 
- Utilizamos el termino *reviciones* para referise a todas las tecnicas estaticas llevadas a cabo por personas.
- Se revisa el codigo buscando problemas 
- El *Objetivo* es criticar al producto, *No se debe utilizar para evaluar a los programadores* 
- *Permiten* remover defectos baratos de forma temprana. Eso dismunuye el tiempo que consumen las pruebas dinamicas. 
- *Permite* obtener un *aprendizaje muto*, ya que se hacen en grupo. unifica y mejora el estilo y metodos de programacion, lo que produce una mejora en la calidad de los proximos productos. 

##### Proceso general de revisiones
- `Planificacion`
- `Kick-off`
- `Preparacion individual`
- `Reunion de revision`
- `Re-trabajo`
- `Seguimiento`

##### Roles y responsabilidades de las reviciones
- `Lider`: *Selecciona* los *artefactos* a ser revisados, asigna los *recursos* necesarios y selecciona el *equipo* de revision. Generalmente *no participa* de las reuniones de revision
- `Moderador`: Responsable de ejecutar la revision. Tambien organiza la discucion.
- `Autor`: Presenta y explica el codigo
- `Revisores`: Expertos tecnicos que participan en la revision
- `Secretario`: Escribe el reporte de la reunion. 
Una persona puede realizar mas de un rol 

##### Tipo de revisiones
- Pueden depender de su *objeto*. 
	- Se puede hacer revisiones de los *productos* generados a partir del proceso de software
	- Se pueden hacer del *proyecto o procesos* de desarrollo. (managment reviews) 
- Algunas revisiones de producto: 
	- **Recorridas:**
		- Se "recorre" el producto en busca de defectos
		- Depende de las capacidad de los revisaores en que mirar, ya que no conctamos con una checklist.
		- EL *Objetivo principal* es descubir defectos, problemas y ambigüedades 
		- Es informal comparado contra las inspecciones
		- Generalmente son en grupos
	- **Inspecciones:**
		- Es uno de los metodos mas formales de revision. 
		- Sigue un *proceso* *formal* y *prescriptivo*
		- Se examina el artefacto (puede tiene porque solo aplicar al codigo)
		- Los inspectores (o revisores) utiliza una *checklist* para el proceso, eso permite que el los mas junior tambien pueda realizar estas inspecciones
		- Algunas cosas que se revisan pueden ser: Uso de variables no inicializadas, asignaciones de tipo no compatible
	- **Revisiones tecnicas:**
		- 
	- **Revisiones informales:**


#### Analisis estatico
- El objetivo es el mismo que las anteriores, encontrar defectos o partes propensas a defectos en los documentos. 
- La *diferencia* es que se utiliza una *heramienta*
- El *documento* (ej codigo fuente) tiene que tener una estructura para poder ser chekeado. 
- Es *estatico* porque no se ejecuta el codigo
- Es mayormente un analisis estatico:
	- Instrucciones bien formadas 
	- Desviaciones de estandares
	- Anomalia en el flujo de control y datos
- Ayudan a *complementar el compilador*. 

### Tecnicas dinamicas
- Se prueba el sistema ejecutandose
- Hay 3 categorias: 
	- Pruebas caja negra (basadas en espesificacion)
	- Pruebas caja blanca (pruebas estructurales)
	- Pruebas basadas en experiencia
- En las cajas blanca tenemos conocimiento interno dentro del componente a probar, y de su estructura se generan las pruebas. 

#### Tecnica caja negra
- En esteas pruebas no se tiene en cuenta el diseño o estructura del objeto de prueba
- Se puede hacer caja negra a nivel que queramos, o sea, de funciones, clases, modulos, sistemas. No tiene porque ser solo de sistema.
- Algunas tecnicas: 
	- **Particion en clases de equivalencia**
		- Se utiliza el concepto de *clase de equivalencia*: Conjunto de entradas para las cuales suponemos que el software se comporta igual
		- Para generar las particiones tenemos el siguiente proceso: 
			1. Indentificar el dominio de entrada y de salida
			2. identificar las clases de equivalencia de ese dominio
			3. Definir los casos de prueba
		- Los casos de prueba son buenos si:
			- Reducen el numero de otros casos de prueba
			- Cubre un conjuntos extensos de otros casos de prueba posibles
		- Como minimo hay que tener dos clases, los *casos valido*s y los *no validos*
		- Si vemos que para dos elemento de la misma clases, el programa los trata de forma difertente => Dividir
		- Para definir los casos de prueba:
			1. Asignar un id a cada clase de equivalencia
			2. Generar tantos casos de prueba que se cubran todas las clases de equivalencia *validas*, intentanto ser lo mas *abarcativo* en estos. Asi minimizamos el numero de casos de prueba
			3. Generar un caso de prueba que solo afecte a una clase de equivalencia *no valida*. Asi se puede localizar un error en la clase de equivalencia erronea. 
		- Para las *clases de entrada* nos enfocamos en dividir la entrada segun como cremos que se va a comportar el programa. 
		- Ej (ejemplo del triangulo)
			- La suma de dos lados es siempre mayor que la del tercero.
			- La suma de dos lados no siempre es mayor que la del tercero.  
			- No ingreso todos los lados.
		- Para las *clases de salida* nos enfocamos en las salidas del programa, no en como llegamos a ellas. 
		- EJ  (ejemplo del triangulo)
			- Triángulo escaleno 
			- Triángulo isósceles 
			- Triangulo equilátero 
			- No es un triángulo válido
		- Un ejemplo de un valor limite de salida podria ser: Triangulo casi valido (lado 1 =1, lado 2 = 2 y lado 3 = 3)
	- **Analisis de valores limites**
		- Probar los limites entre las clases de equivalencia.
		- Probado el limite entre las clases y sus adyasentes.  
		- Ej: La entrada son valores entre -1 y 1 Escribir casos de prueba con entrada 1, -1, 1.001, -1.001
	- **Prueba de transicion de estados**
	- **Prueba basadas en la logica**( Grafos causa efecto, tablas de decision y pairwise testing)
	- **Prueba basadas en caso de uso**

## Tecnicas de caja blanca
- La generacion de los casos de prueba se basan en *la estructura y diseño del objeto de prueba*
- Tambien se las conoce como *tecnicas basadas en la estructura o el codigo*.
- Estos criterios no son muy bueno para generar casos de prueba, pero si para poder *evaluar casos de prueba*. Generado con otras tacticas, como la de clases de equivalencia o valor limite. 
- Hay dos tipos
	- Basada en el *flujo de control* del programa. El cubrimiento del testing se mide en termino del *grafo del control* del programa (o sea la escrutura de if - else - while, etc)
	- Basada en el *flujo de datos* del programa. El cubrimiento del testing se mide en termino de *asociaciones definicion-uso* del programa. 

#### Criterio de cubrimiento
El foco de este tipo de tecnica es cubir cada parte del codigo al menos una vez. Hay varios criterios:
- **Cubrimiento de sentencias**: El conjunto de casos de prueba ejecutan cada instruccion del codigo al menos una vez. Este criterio es muy debil. *Necesario no suficiente*
- **Cubrimiento de decision**: Cada decision (condicion dentro de una estructura condicional) dentro del codigo toma al menos una vez el valor true y otra false. 
- **Cubrimiento de condicion**: Eso lo que significa es que dentro de una decision, cada condicion (termino) debe tomar el valor true y el false
- **Cubrimiento de condicion multiple**: Cada combinacion posible de condicion dentro de una decision se debe ejecutar al menos una vez
- **Cubrimiento de decision/condicion**: Es que se cumple tanto el de decision y el de condicion
- **Cubrimiento de arcos**:
- **Cubrimiento de caminos**: Dado el grafo control, se ejecutan una vez todos los caminos posibles (combinaciones de trayectorias)
- **Cubrimiento de trayectorias independientes**:

## Tecnicas basadas en la experiencia
- Aunque no tengamos la espesificacion o el codigo, podemos pronar
- Este enfoque es *muy utilizado*
- No es un metodo sistematico, o sea no hay un procedimiento. Se basa *fuertemente* en la intuicion, habilidades, conocimiento y experiencia del tester. 
- Se basan en *datos historicos* (defectos pasados) o en la *intucion de donde podrian estar en el futuro* (*error guessing*)
- **Importante**: Si no existe documentacion para utilizar como base del testing, se puede emplear la tecnica de *testing exploratorio*. 
- 3 Actividades son realizadas de forma simultania durante este tipo de testing
	- Aprendizaje de la aplicacion
	- Diseño de casos de prueba
	- Ejecucion de casos de prueba
- No hay una actividad explicita de planificacion
- Se puede utilizar un enfoque llamado por *sesiones*. 
	- Durante la secciones nos fijamos objetivos a cumplir durante la seccion (Ej: ver integracion con otras app, robustez, flujos de la app, etc)
	- En base a los resultados de secciones previas, se planifican nuevas sesiones utilizando una "hoja de ruta"
	- *Limitar el tiempo* dedicado a cada sesion
- Las *primera secciones* tiene un *enfoque a obtener conocimiento del software*, por lo que se ejecutan pocos casos de prueba. Asi se derivan el comportamiento del software (que es, como funciona, problemas de calidad potenciales, que expectativas deberia cumplir)
- La tecnica es *altamente dependiente de las habilidades del tester*. En su forma de pensar y en su conocimiento
- Algunas *preguntas importantes* a realizarse en cada seccion de prueba son: 
	- ¿Cual es el objetivo?: Recordar que la secciones tiene diferentes objetivos. 
	- ¿Que debe ser probado? Ahi nos podemos enfocar en determinadas partes del programa
	- ¿Que metodos de prueba debo usar? Podemos usar cualquiera de los que ya vimos
	- ¿Que tipo de problema podria encontrar? Eso depende del conocimiento/experiencia del tester para poder responder a esta pregunta
- Los Casos de prueba ejecutado, *tiene influencia* en el diseño y ejecucion de los proximos
- El tester construye un *proceso mental* del software (dependiendo de lo que conosca del software y del negocio), y prueba contra ese modelo, por lo que las fallas que encuentre seran *posibles fallas*


## Elegir la mejor tecnica
- Cuales pruebas deberia usar? 
- Algunos factores: 
	- **Objeto de prueba**: Por ejemplo, probar un sistema integrado, haciando pruebas de cubrimiento de sentencias es practicamente imposible.
	- **Documentacion formal y/o disponibilidad de heramientas**: Si no hay documentacion o espesificacion hay determinadas tecnicas que no son viables. Para otras sin heramientas tambien es inviable, por ejemplo ver el coverage de la aplicacion.
	- **Cumplimiento de estandares** : hay veces que el producto tiene que satifacer determinandos estandares, en esos casos, dichos estandares pueden influir en la tecnica para probar 
	- **Experiencia de los testers**
	- **Deseo y necesidades del cliente**
	- **Evaluacion de riesgos**: Dependiendo de que funcionalidades tienen mas riesgo, se puede analizar la mejor tecnica para la misma. 

![[Pasted image 20230516015825.png]]

- **Sugerencia**: "Jacobson sugiere ejecutar *primero las pruebas de caja negra* y cuando estas sean todas correctas completar con caja blanca. Esto se *debe a que la caja blanca depende del código* y cuando se detecten errores con caja negra el código cambia al corregir los errores detectados."

## Comparacion de tecnicas

#### Estaticas 
##### Ventajas
- *Efectivas en la detección temprana de defectos*. No tengo porque tener el sistema integrado,  incluso se puede aplicar nivel de requisitos, modelo, etc (previo a la implementacion)
- *Sirven para verificar cualquier producto (requerimientos, diseño, código, casos de prueba, etc)*
- *Conclusiones de valides general*: Generalmente cuando se prueba en dinamico, la valides esta acotado al contexto, aqui no, la valides de esta prueba es general al ambiente. 

##### Desventajas
- *Sugeto a errores de nuetro razonamiento*: Este testing depende mucho de nuestra interpretacion, que puede estar mal. Ademas de nuestra experiencia. 
- *No se usan para validacion, solo verificacion*: La validacion la hace generalmente el cliente con el software funcionando.
- *No consideran el hardware o el software base*

#### Dinamicas 
##### Ventajas
- *Consideramos el ambiente donde es usado* por lo que es mas realista 
- *Sirven para verificar y validar*
- *SIrven para probar otras caracteristicas ademas de funcionalidad*

##### Desventajas
- *Depende del contexto donde se ejecute*
- *Solo podemos asegurar los casos probados, por lo la generalidad no es clara* 
- *Solo sirve para probar el software construido*, no para requisitos o cosas que aun no estan finalizadas 
- *Normalmente se detecta un único error por prueba* (los errores cubren a otros errores o el programa colapsa)


## Pruebas no funcionales
- Tambien se las conoce como *prueba de desempeño*
- Tiene como objetivo probar un requisito no funcional, por ejemplo el tiempo de respuesta.
- Se tiene que fijar un *criterio de aceptacion* alcanzable
- Este tipo de pruebas es *muy sensible* al *ambiente*, por lo que debemos de conocer sus caracteristicas. 
- En muchas de estas pruebas, como por ejemplo la de volumen, tambien precisamos *datos*, y a veces un gran volumen de estos datos y tiene que ser consistente.
- En las pruebas de carga, en las de voluemn, debido al numero de recursos requeridos para realizar la prueba, se requieren *heramientas*, tener conocimientos de este tipo de pruebas y un buen manejo de la *gestion de la configuracion*

#### Tipo de pruebas no funcionales
- **Prueba de carga**
	- Esta prueba me dice lo minimo que el sistema debe poder soportar, osea prueba el *nivel de carga*.
- **Prueba de performance (rendimiento)**
- **Prueba de volumen**
- **Prueba de estres**
	- Aqui expando los *niveles de carga* (en relacion a la prueba de carga) para ver a partir de que punto el sistema se degrada. Pero ese nivel supera por lejos a la carga minima requerida probada en la prueba de carga
- **Prueba de seguridad**
- **Prueba de confiabilidad**
- **Prueba de robustez**
- **Prueba de compatibilidad y conversion de datos**
- **Prueba de configuracion**
- **Prueba de facilidad de uso**
- **Comprobacion de documentacion**
	- Mas que una prueba es una *revision*
	- Esto tiene un sentido mas de *manual de usuario*