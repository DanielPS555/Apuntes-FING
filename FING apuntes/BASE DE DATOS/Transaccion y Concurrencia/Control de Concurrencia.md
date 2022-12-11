En una BD se podrian ejecutar muchos procesos concurrrentemente sobre exactamente los mismos datos. Los datos puede interferir entre si. 
![[Pasted image 20221119202444.png]]

El  *Control de concurrencia* es la corrdinacion de procesos concurrentes que operan sobre datos compartidos y que podrian interferir entre ellos. 

Las *transaccion*  son los procesos concurrentes que se ejecutan sobre datos compartidos. Tiene que cumplir con las propiedades *ACID*. Garantizando:
- *Atomicidad*: Desde un punto de vista del resultado, o se ejecuta toda la consulta o nada.
- *Consistencia*: Siempre lleva a la base de un estado consistente o otro consistente 
- *Aislamiento*: Por mas que los datos sean los mismos, las transacciones no deberian alterarse entre si. 
- *Durabilidad*: Los cambios de una transsacion confirmada debe ser permamantes

## Estados de una transaacion

![[Pasted image 20221119203243.png]]
Si una transacion pasa por el estado de falla, es como si nunca se ubiera ejecutado la transaccion. 


## Definiciones y notacion
### Operaciones
![[Pasted image 20221119204022.png]]
![[Pasted image 20221119204037.png]]

El item de dato es un dato del disco, puede ser un registro, un bloque, etc. Pero del disco.
Una vez que se hace el commit no se puede hacer un abort. 

El manejador de transacciones toma los transacciones y re ordena las operaciones de forma tal de implementar ACID hasta donde pueda. No puede cambiar el orden de las operaciones de las transacicones. Puede añadir operaciones como abort y commit. 
![[Pasted image 20221119205443.png]]

La *historia* es la ordenacion de las operaciones de la transsaccion. 
Se le llama una *historia serial* y estan en el mismo orden que las transaaciones (una tras de la otra)
 y *historia entrelazada* sino. 
