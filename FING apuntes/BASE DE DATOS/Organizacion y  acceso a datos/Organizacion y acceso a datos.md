Lo que se ve en este documento no se aplica a todos los manejadores de base de datos (DBMS). 
Un esquema de la arquitectura podria ser el siguiente: 

![[Pasted image 20221030155814.png]]


## Organizacion fisica de los datos
Lo que nosotros queremos manejar (a nivel de BBDD) son tuplas, o tambien llamados *registros*. Estos registros son *archivos* , estos estan el en file system en bloques de disco. La forma de tratar esto depende del disco y del SO. Estos bloques con la unidad de tranferencia entre el disco y la *memoria*. Los datos deben estar disponibles en memoria, donde se lee de *buffers*. 


Los propios DBMS toman una particion de disco o un gran archivo. Y usan dicha area como su propio disco. 
Re implementan estructuras de datos, algoritmos de manupulacion y de ordenamiento. A igual que los mecanimos de buffering y de paginado. 

Por lo general los archivos se leen de forma secuencial. ¿eso es bueno para las DBMS?

![[Pasted image 20221030162921.png]]

solamente en el JOIn, si el tamaño es de M empleados y de N departamento. Requerimios M * N operaciones con acceso a disco. Eso es muy costoso. Se puede mejorar con otras estructuras de datos que  faciliten el acceso, se llaman *indices*. El indice es como una tabla con un atributo identificador y un puntero al registro.
![[Pasted image 20221030163351.png]]


### Tipos de indices
#### Fisicos vs Logicos
- `Fisicos`: Estos inidices a hacer referencia a ubicaciones en el disco 
- `Logicos` Estos indices hacen referencia a otros indices fisicos
#### Ordenados vs No ordenados
Requieren o no que los datos a indexar esten ordenados en el disco. 
#### Densos vs no densos
Tiene a todas las claves o solo a algunas

### Indices que requieren ordenamiento
#### Indice primario
Es por cada clave primaria, se tiene la direccion del disco (bloque o bloque + offset)

#### Indice de agrupamiento (cluster index)
Sobre un atributo que no es clave primaria
Si se me dice el bloque, tengo que buscar en todos los registros del bloque. Es posible que el volumen de datos sea de varios bloques, en ese caso se utiliza una lista .

### Indices que no requieren ordenamiento
#### Indices secuncario
Se cream ima estructura auxiliar ordenada con el campo a indexar. Por cada valor un puntero o una lista de punteros. 

### Estructura para los indices
Se pueden estructurar por *HASH*, es muy bueno para la inserecion y recuperacion por condicion de igualdad. Es malo para condicion con relacion de orden. 

Tambien se puede utilizar *Arboles B o B+*, tiene un buen comportamiento para recuperacion por orden de igualdad como de orden. Tambien en insercion. Pero ocupan mucho mas espacio en disco. 

### Compartacion de estructuras

Se comparan la estructuras en funcion a la cantidad de operaciones basicas resultante de las operaciones sobre la estructura. Solo importando las operaciones de I/O y no de memoria porque son despreciables. 

Hay que tener en cuenta que un bloque de disco puede tener varios nodos de datos. Y por lo general cuando se lee un bloque, se leen varios bloques contigous, por lo que lo hace mas eficiente. 

