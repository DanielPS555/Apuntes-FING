
## Como se resuelve las consultas
![[Pasted image 20221102222452.png]]

Vamos a ver estrategias usuales para la optimizacion, en particular:
- Proceso detallado de Optimizacion
- ``Optimizacion Heuristica``: Se basa en *equivalencias* de expreciones de algebra y ciertas estategias para liitar el tamaño de los resultados
- ``Optimizacion por costos``: Basada en *estimaciones*y datos del catelogo que permiten seleccionar un mejor plan de acceso. El costo en base de datos es la cantidad de acceso.

## Proceso de optimizacion
Comenzamos desde el *abrol sintactico* que genero el *parcer*. A partir de ese abrol geneamos un *arbol canonico*, del cual generaremos a su vez varios (o uno) *planes logicos con tamaño*. Estamos planes logicos nos dicen las operaciones logicas que deberemos hacer, apartir de ellos haremos generaremos los *planes fisicos*, y en base al *costo* eligiremos uno de estos planes.


![[Pasted image 20221102223238.png]]

El abrol canonico es uno solo, y siempre se genera igual. Primero la proyeccion, luego la seleccion con todas las condiciones con and. Luego los tablas del  from cruzadas con productos cartecianos en el mismo orden que estan en el from  y tiene que ir dos a dos, estas tablas de hacen join de forma tal que esta 'recortado a la izquierda', osea, el siguiente producto carteciano se hace en el hijo de la isquierda   *TIENE QUE SER ASI, sino esta mal.*. 

![[Pasted image 20221102224154.png]]

Luego el generador de planes logicos generan planes logicos, utilizan heuristicas y se agregan datos de tamaño, que son datos que se utilizan para mejorar la velocidad de las consultas. 

![[Pasted image 20221102224421.png]]

Una vez que tenemos el plan logico. Por medio de otros datos (el tamaño de las tablas, la selectividad, sobre que estan implementados los indices, etc) se elige las implementaciones de cada operacion. Por ejemplo en el join podemos elegir un loop anidad, un loop unico, un sort merge, etc.
![[Pasted image 20221102224708.png]]

Luego para elegir el plan fisico, mi unidad medida es el numero de bloques de disco que se deben acceder. 
![[Pasted image 20221102224845.png]]

En resumen: 

![[Pasted image 20221102224916.png]]

