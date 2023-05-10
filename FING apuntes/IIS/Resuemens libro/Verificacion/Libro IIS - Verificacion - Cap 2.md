
## Dudas 
- [x] A lo que en el libro llaman Test Extent es lo que se referien con "Grado de prueba"? 
- [x] La verificacion de un nivel va contra el insumo de ese nivel o contra los requisitos originales?
- [ ] Verificar el principio de contexto-dependiente segun el video y el libro

## Terminologia
- Los terminos son muy confusos
- *Def (Fallas):* "La falla es lo que experimentamos en el sistema, es algo externo. La falla es algo que el sistema no hace, o hace y no lo deberia hacer, o no no lo hace y los deberia hacer, o lo hace mal". 
	*El software falla cuando no hace lo que deberia*
	Ojo, estamos asumiendo que no hay condiciones externas que puedan probocar una falla en el sistema, por ejemplo corriente. 
- *Def (Faltas o Defectos):* Una falla SIEMPRE es causada por una Falta o un Defecto. Esto es un error en el software, el cual no tiene porque causar una Falla pero puede.  
- *Def (Errores):* Las Faltas o defecto POR LO GENERAL son causadas por un error humano. Por ejemplo no entendi los requisitos. Puede ser que los errores humanos no generen una Falta. 

#### Cuales son algunos motivos para un fallo (osea un defecto)
- La espesificacion no estipula exactamente lo que el cliente precisa o quiere (requisitos faltantes o incorrectos)
- Requerimientos no se pueden implementar
- Defectos en el diseño 
- Defectos en el codigo


#### Objetivo  
- El *Objetivo* de a verificacion y validacion (V & V) es *detectar y corregir estos defectos antes de liberar el producto*. 

- Algunos objetivos de V & V son:
	- Ejecutar el programa para provocar fallas (una forma de encontrar fallas)
	- Ejecutar el programa para medir su calidad 
	- Ejecutar el programa para generar confianza. 
		Un atributo de calidad del software se llama *confiabilidad* se mide en cantidad de fallas por unidad de tiempo 
	- Analizar/revisar el programa o su documentacion para detectar defectos (y prevenir fallas) (*Esto no es testear sino prevenir la falla antes que esta aparezca* )

#### Testing != Debuggin
- **Testing NO es debugging**
	- **Testing:** Simpre revision del comportamiento del software mediante su ejecucion.
	- **Debugging:** Actividad de localizar el defecto en el codigo y corregirlo.

#### Probar != revision
- Para *probar* el codigo, el mismo se tiene que ejecutar, si no se ejecuta es una *revision*


#### Otras terminologias importantes 
- *Test scenarios:* Conjunto de Casos de prueba convinados. Donde el resultado de un caso de prueba puede ser el punto de inicio de otro. 
- *Objeto de prueba o tipo de prueba*: Es el proposito de la prueba. Por ejemplo "Load test"
- *Tecnica de prueba*: Es la tecnica que se aplico para espesificar o ejecutar los test
- *Objeto de prueba*: Tipo de objeto que se esta probando (Ej: GUI)
- *Nivel de prueba*: Se refiere al nivel de prueba, y depende del ciclo de vida, algunos segun el modelo en V son la prueba de aceptacion, prueba de sistema, prueba de integracion y prueba unitaria. 
- *Perfil de persona que prueba*: Es el perfil que tiene la persona que esta realizando las pruebas (EJ: Desarrolador)
- *Grado de prueba*: Indica con cuanta profundidad se realizan las pruebas. 
- *Base de prueba:* Se refeire a cualquier entrada de informacion utilizada para el test process, un ejemplo claro es la documentacion. 
- *Caso de prueba*: Defie las condiciones de prueba, tambien las precondiciones de ejecucion, sus entradas, salidas esperadas del objeto de prueba.
- *Test oracle (oraculo):* Es un mecanismo para predecir el resultado esperado. Hay dos principales oraculos: 
	- La espesificacion
	- Una funcion que haga la accion invesa (se puede ver si lo que tenemos hecho esta bien en base a ver si la composicion es la identidad)
 
#### Otros apartados importantes a tener en cuenta
- Cuando se reparan defectos por lo general se aumenta la calidad del producto si no se introducen nuevos defectos o muchos defectos [Opinion]
- Luego de una modificacion no solamente hay que repetir los test, sino que hay que crear nuevos para curbir efectos secundarios
- Cualquier *ejecucion* del objeto de prueba con el fin de examinarlo **se lo conoce como testing**.
- Ademas se la ejecucion del Test object con la Test data, *planning*, *design*, *implementation* y *analysis* (Lo que se conoce como *test managment* ) tambien es parte del *test process*. 
- Los *Casos de prueba* contienen los *Test conditions*.
- Aunque los casos de prueba no muestren fallas, no podemos concluir que no hay fallas o que futuros casos de pruebas no la puedan encontrar. 
- Los defectos nos dan mucha informacion acerca de como desarrolo, sino tambien del proceso de desarrolo, y por ende me sirve para mejoralo. 

#### Verificacion != Validacion
- La **Verificacion** se pregunta ¿estamos construyendo el producto *correctamente*?
	- Busca comprobar que el software esta de acuerdo con su espesificacion
	- Aqui surge el *Testing de defectos *
- La **Validacion** se pregunta ¿Estamos construyendo el producto *correcto*?
	- Se busca comprobar que el software hace lo que el usuario espera
	- Aqui surge el *Testing de validacion*

#### Principios de testing
- **El testing muestra la presencia de defectos, no la ausencia de ellos**

- **Testing exactivo no es posible**

- **Las actividades de testing (V&V) deben comenzar lo antes posible**

- **Agrupamiento / aglomeracion de defectos (defect clustering)**
	Los defectos no estan uniformemente distribuidos, se encuentran por lo general agrupados
- **La paradoja de persistencia**
	Si un test se repite una y otra vez tiende a perder la efectividad. Nuevos y modificados test cases deben ser desarrolados y añadidos 
- **El testing es contexto-dependiente**
	La intensidad del testing, los criterios de salida, etc se deben determinar en base al ambiente de uso (por ejemplo a los riesgos de ese ambiente). 
	Dos sistema no deberian ser testeados de la misma manera. 
- **Decir que el software es util porque "no se expermimentan fallas " es una falacia**


#### Puedo probar sin una espesificacion? 
Si, aunque no se tenga la espesificacion, el conocimiento del dominio es fundamental para realizar pruebas. 
A esto se lo llama *Testing exploratorio* [Falta buscar mas informacion de esto]. La idea de esto es ir explorando durante el desarrolo del testing.  


### Formas para detectar defectos
- Una forma clara es realizar casos de prueba en base a las posibles salidas esperadas.
- Otra forma es revisar el codigo. 

### Clasificacion de defecto
- Hay muchos tipos de clasificaciones de defectos. Un ejemplo podria ser:
	- La fuente del defecto
	- Donde se encuentra
	- Prioridad (severidad)
	- Tipo de defecto
	- Si es defecto en los requisitos o si es en la implementacion
	- De que tipo es (mirar ppt 13 de V&V clase 1)
- ¿De que sirve clasificarlos? 
	- *Nos guia en la orientar la verificacion*:  Si se el tipo de defecto que se suele cometer, puedo ir a buscalo expresamente
	- *Mejorar el proceso*: Si identificamos la fase en la cual se introducen muchos defectos, me focalizo en la mejora de esa parte.