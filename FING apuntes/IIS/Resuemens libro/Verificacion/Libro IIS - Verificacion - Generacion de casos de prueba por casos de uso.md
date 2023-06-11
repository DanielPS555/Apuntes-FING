# Dudas
- [ ] Cuando se dice "Es necesario incorportar las condicones de borde en cada escenario" ¿Significa que los datos elegidos deben ser de borde o que?

# Segun los articulos

- Aunque se utilize entre un 30% a un 50 % de los recursos para el testing. Muchos considera como *insuficiente* el testing previo a salir a prod. 
- Eso sucede generalmente por el testing es:
	- Un proceso de propocion dificil (WTF???)
	- Se realiza sin ninguna metodologia clara 
- En la industria (Tambien en RUP) muy bien recibido *comenzar el testing lo antes posible*. 
- Tener un *metodo claro* de como hacer el testing ayuda a incrmental el coverage, eficiencia, y la calidad del software. 
- En esta seccion se trabaja en como generar casos de prueba a partir de casos de uso para: 
	- Comenzar con el proceso cuanto antes 
	- Brindar una metodologia de testing
- Los CU definen los requisitos del sistema, por lo tanto disponemos de ellos en un punto temprano del ciclo de vida. 
- En particular *los CU dicen al usuario que esperar, al desarrolador que programar, el escritor tecnico que docuentar y al tester que testear*

- La generacion de los *casos de prueba* son la 1º etapa para el proceso de testing. Luego se diseñan los *procesos de prueba* y por ultimo los *test scripts* son implementados.
- Los casos de prueba *identifican* y *comunican* las condiciones que se deben cumplir para verificar que la implementacion es exitosa con los requisitos. 


## Casos de uso
- Los CU se pueden ver en forma de digrama, donde los ovalos son los CU y los actores son las personas o sistemas externos que interactua con el CU. 
- Este digrama nos muestra una foro a gran escala. 
- Los CU se deben expandir agregando sobre todo dos cosas: el *flujo basico* y los *flujos alternativos*.
- En ambos casos los flujos se deben escribir como una *serie de pasos*. Cada paso idealmente es una conversacion entre el actor y el sistema, *explicando que hace el usuario y que hace en respuesta el sistema*. 

## Esenarios de CU
- Un *esenario de caso de uso* es una *instancia* de un *caso de uso*. Tambien se lo puede ver como un caminio completo a travez del CU. 
- Mirar los ejemplo de los articulos. 

## Generando los Test case (Por CU)
- Un Caso de prueba es una *serie de inputs, condiciones de ejecucio* y *resultados esperados*.
- El el *uso* es verificar el cumplimiento de los requisitos. El *propocito* es identificar y comunicar las condiciones con las cuales seran implementadas los test.
- El proceso de la generacion de estos casos de prueba consiste en 3 pasos: 
	1. Para cada CU, *generar un completo conjunto de esenarios* de CU
	2. Para cada esenario *identificar al menos un caso de prueba* y las *condiciones necesarias para que el mismo sea ejecutable*. 
	3. Para cada casode prueba, identificar los *valores con los que se prueban*

#### Paso 1 (generar esenarios)
- Leer los CU y identificar cada combinacion del flujo base y los flujos alternativos.
- Generar una tabla con las convinaciones. 

#### Paso 2 (identificar los casos de prueba)
- Ideralmente se deberia poder generar *al menos un* caso de prueba por cada esenario. 
- Hay veces que hay que agregar mas de un caso de prueba por escenario. 
- Tambien podemos añadir casos de prueba para los casos limites. 
- Tambien tenemos que identificar las *condiciones* para ejecutar los escenarios. 
- En la tabla resultante se encuentran un *ID* por esenario, una *descripcion*, en la ultima columna el *resultado esperado*. En todas las del medio, van los datos que se requieren los test. 
- A esta altura en todos estos datos extras, hay solo 3 posibles estados: *V* (Dato valido), *I* (Dato invalido) y *N/A* (No es necesario para ese CU)

#### Paso 3(Identificar valores para los datos de prueba)
- Hay que revisar y validar los casos de prueba para verificar su *que sean adecuados*, no haya *redundancia* ni *faltantes*
- Luego sustituimo los valores de *V* e *I* por valores de verdad. 


# Notas de la clase 
- El grafo que se genera al flujo base y al alternativo se llama *flujo de control*. Este muestra donde comienza cada alternativo y donde retorna o termina. Es la 2º pag de la 3º PPT de V & V.
- Cuando se generan los escenarios mirando el flujo de control. Al menos hay que generar tanto esenarios para *cubir todas las aristas*. Tambien nos pueden interesar pasar varias veces por un flujo de alternativo (tipo blucle) o combinar varios alternativos en un mismo escenario. 
- Para mi mismo esenario podemos tener *mas de una condicion*, en ese caso debemos probar todas las condiciones de ese esenario. A eso se lo llama *esenario-condicion*.
- **Importante:** Si en el la tabla escenario - Condicion tenemos filas repetidas, significa que falta alguna condicion mas a considerar (columna). 
- Si un esenario se puede ejecutar con mas de una condicion, divido el escenario en varias escenario-condiciones
- Cuando tenemos para un mismo escenario diferentes condiciones compatibles, entonces se lo escribe en la tabla como ESC*N*C*M* donde N y M son indices
