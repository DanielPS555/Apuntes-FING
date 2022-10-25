Teniamos el MER que era un *esquema conceptual*, el cual descriia la realidad. Por otro lado el *esquema logico* se preocupa como escribir las base de datos.

En este documento vamos a ver el pasaje. 


Hay reglas que se deben cumplir 

## Dependencia de inclusion 
Es una restricion sobre el modelo relacional, expresa que una proyeccion de unos atributos de una tabla debe estar incluida en la proyeccion de otros atirbutos en otra tabla.

![[Pasted image 20221022025908.png]]

*Las claves foreaneas  son un caso de esto*

## Reglas 

### Entidades
- Para cada entidad, se crea una tabla, por cada *atributo simple* se crea un atributo en la tabla
- Para cada *atributo estructurado*, se crean tantos atributos como hojas tenga. 
- Se selecciona como *clave primaria* un determinante, el resto de ls determinante deben ser *claves alternaticas*
- Para los atributos mulivaluado, se crea una nueva tabla con la informacion del multivalorado y la clave primaria de la entidad. ![[Pasted image 20221022030255.png]]
- Ojo que esta pareja de relaciones tiene ir con una dependencia de inclusion. En este caso que la proyecion de cedula de TELEFONOS este incluido en la proyecion de cedula con PERSONAL

### Relaciones BInarias N:N
- Por cada una de estas relaciones creamos una tablam donde se colocan las claves primerasias de las tablas participantes.  Tambien añadimos los atributos de la propia relacion, que se tratan al igual que los atributos de una entidad.
- Hay que poner las dependencias de inclusion 
- Las totalidades generan relaciones de inclusion en el sentido inverso 

### Relacion binaria 1:N
Hay dos casos:
- **1:N sin totalidad del lado N**
	Se trata igual que una N:N, solo que cambia la clave primaria de la relacion, que es la misma clave que del lado N
	![[Pasted image 20221022032839.png]]
	Notar que aqui evitamos NULLs

- **1:N con totalidad del lado N**
	Aqui ponemos la clave de la entidad con el lado con cardinalidad 1, en la entidad con cardinalidad N. Aqui evitamos null.
	![[Pasted image 20221022033144.png]]
EN estos casos los propios atributos de la relacion estan en la entidad del lado con cardinaliad N

### Entidad debil
- Se procede igual que con las relaciones 1:N y totalidad del lado N. 
- La clave de la tabla es la clave de la entidad fuerte + identificador parcial. 
![[Pasted image 20221022033510.png]]


### Agregaciones
Aqui tratamos a la agregacion (a la relacion que agrega) como  una entidad, luego no tiene mas misterio. Si otra relacion se relaciona con nuestra agregacion, tiene una *dependencia de inclusion* con la relacion que genera la agregacion. 
![[Pasted image 20221022034645.png]]


### Categorizacion 
Hya 4 formas, dependiendo del caso 
1. **General (siempre funciona)**
![[Pasted image 20221022040201.png]]


2. **Solo con categorizacion total** 
![[Pasted image 20221022040218.png]]
Notar que esto usa vistas (en este caso la tabla Personal)

3. **Solo si son todas disjuntas**

![[Pasted image 20221022040342.png]]

4. **Puede o no ser disjunta (para mi esto es un asco)**
![[Pasted image 20221022040349.png]]