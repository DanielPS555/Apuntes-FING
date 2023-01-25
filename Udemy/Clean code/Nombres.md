Vamos a ver como asignar buenos nombres 
- Los nombres tiene que ser meaningful 

## Puntos de aplicacion

### Variable & Constants 
- Tiene que ser *sustantivos* o *fraces cortas con adjetivos*
- La idea es que los nombres provean el mayor detalle posible, siempre y cuando sea de utilidad para el contexto. Por ejemplo, si tengo usuarios no loggeados y usuarios loggeados,, es mejor que si un usuario esta loggeado se llame `authenticatedUser` en vez de solo `user`. 
- No añadir redundancia y hacer los nombres super largos
- Para el caso de boolean, los nombres tiene que ser *preguntas que se puedan responder con verdadero/falso*

### Metodos
- tiene que ser *verbo* o *fraces cortas con adjetivos*
- La idea es que el nombre debe describir la operacion, osea lo que hace. Nuevamente queremos dar los maximos detalles sin introducir redundancia. 
- Para el caso de las boolean, estamos describiendo el resultado y no lo que hace la operacion. Ademas el nombre tiene que ser una pregunta. Por ejemplo `purchase.isPaid()` o `isvalid()`.
- En los lenguajes que los get y los set se trabajan como propiedades (como es el caso de js), el nombre de los get y los set no tiene que tener el prefijo 'get' ni 'set' delante

### Clases
- Tiene que ser *sustantivos* o *fraces cortas con adjetivos*
- Poner nombres que describan el objeto 
- No añadir redundencia
- No poner sufijos al pedo. Por ejemplo DatabaseManager no tiene sentido si es una clase instanciable, si si es static. 


### En general
- Hay que evitar redundancia en los nombres. Ejemplo no poner `userWithName` si el user ya tiene un name dentro. Evitar el uso de jerga, abreviaciones no claras o nombres que indiquen cosas que no son.
- Ser consistente con los nombres, si usas get, mantenete con get
- Usar nombre distintivos 
-  


## Name casing

### snake_case
Se separan las palabras por " _ ". Se usa por ejemplo de Python, especialmente en las variables, funciones y metodos.

### camelCase
Primera letra en minuscula y cada nueva palabra va en mayuscula. Se pusa por ejemplo de java script. 

### PascalCase 
Igual a camelCase, solo que la primera letra esta en mayuscula

### kebab-case 
Se separan las palabras por "-". Se usa en las etiquetas de HTML. 




