 Es cuando le asociaos a cada operador del plan logico una implementacion. Por lo que un mismo plan logico puede generar multiples planes fisicios. 
Para elegir un plan fisico se debe estimar el costo (cantidad de operaciones de I/O) de los diferentes planes que se genereren.

## Parametros para la estimacion
![[Pasted image 20221103005747.png]]
![[Pasted image 20221103011546.png]]

## Implementacion de los operadores 

Hay dos estrategias de implementacion:
- `Pipeline`: Los operadores se ejecutan simultaniamente y pueden pasarse los resultados a medida que se generan. No se graban resultados intermedios
- `No pipeline`: Los operadores se ejecutan secuencialmente y es necesario grabar resultados intermedios
Se anumo que las proyecciones son pipeline, por lo que no tiene costos intermedios. Mientras que las selecciones y los join son no pipeline y hay que considerar los costos intermedios. 

Solo consideramos las operaciones de *lectura* y de  *grabacion*. Todas las operaciones se realizan en unidades de *bloque*, que puedentontener registros de indice o datos. 
El costo de grabacion **siempre** es el costo de grabar todo el resultado. 
![[Pasted image 20221103012507.png]]
Osea esto se añade luego del costo de la lectura de la operacion cuando se tiene que grabar el costo intermedio. 


### Implementacion de seleccion
#### Busqueda lineal
![[Pasted image 20221103012640.png]]

#### Busqueda binaria
![[Pasted image 20221103012751.png]]
La parte final del costo de lectura se da cuando tenes que traer un numero de registros que supera la capacidad de un bloque. Eso es debido a que ya encontraste el 1º bloque que tenia parte de la seleccion, luego el resto de esos registros estan en algunos bloques que estan a continuacion, bueno esos bloques se cuentan con los ultimos 2 terminos de esa formula. 

#### Por indice primario o cluster 
![[Pasted image 20221103013250.png]]
Notar que lo primero es buscar la referencia en el indice y luego es ir a buscar el/los bloque/s.

#### Por indice HASH
![[Pasted image 20221103013952.png]]

#### Indice secuncario con b+
![[Pasted image 20221103014015.png]]
Es `s` y no $s/bf_R$ porque puede pasar que al no erar ordenados los registros en el disco, cada registro puede perteneceser a Bloques diferentes. 


### Implementacion del Join ( $R\Join_{A=B}S$ )

#### Loop anidado por registro 
![[Pasted image 20221103014551.png]]

La primera parte del costo es el que tenemos por traernos todos los posibles valores de R. Luego la srgunda parte es por cuantas veces hay que recorrer todos los bloques de S para encontrar a sus correspondientes. 

#### Loop anidado por bloque
![[Pasted image 20221103015120.png]]
En cada buffer podemos meter 1 bloque en memoria. La idea es tener varios bloques de R en memoria y poder comparar cada bloque que traigamos de S con todos los que tenga en memoria de R. Esos dos buffer que se restan se reservan para S y para el resultado. 

#### Sort-merge join
![[Pasted image 20221103015625.png]]
Va recorriendo las dos tablas a la vez y va machando

#### Index Join
![[Pasted image 20221103015717.png]]
El `h` es el costo dependiendo del hash.

**Super importante** Los indices sirven siempre y cuando estemos en la tabla original, NO LOS PODEMOS USAR EN RESULTADOS INTERMEDIOS.

### El resumen 
![[Pasted image 20221103022023.png]]
![[Pasted image 20221103022029.png]]
