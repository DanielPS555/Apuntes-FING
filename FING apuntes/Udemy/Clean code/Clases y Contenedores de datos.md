## Diferencia entre un Object y un Data container

Hay una diferencia sustancial entre estos dos conceptos : 
`Objetos`
- Tiene atributos privados
- Exponen una serie de metodos (API)
- tiene logica
- Tiene una capa de abstracion sobre los datos que tiene.
`Data container`
- Casi no tiene atributos privados
- No tiene practicamente una API
- Solo contiene y transporta la informacion
- No hay abstracion sobre ellos


## Tamaño de las clases
- Por lo general preferimos *muchas pequeñas clases* que una clase gigante.
- Hay un concepto llamado *Single-Responsibility Principle*(SRP) el cual es que las clases solo deben tener una unica responsbilidad. Osea una clase puede hacer muchas cosas, pero debe tener una sola responsabilidad.

### Cohesión
Esto habla de que tanto los metodos de la clase usan las propiedades de la clase. 
En *Maximun Cohesion* todos los metodos usan cada una de las propiedades de la clase. Y en *No Cohesion* ningun metodo usas ninguna propiedad de clase. Lo que termina ciendo una Data Structur con utility methods. 

Nosotros buscamos *Highly cohesive classes*, osea que todas las clases usen alguno de propiedades de la clase, tendiendo a Maximun cohesion


## Law of Demeter 
Se basa en el pricipio de *Least knowledge*. La idea es que no dependeas de la forma interna de extraños. Osea de objetos que directamente no conosco. 
La regla dice que el codigo dentro de un metodo solo puede acceder a las propiedades y metodos de: 
- El objeto al que pertenece (Osea puedo llamar a cualquier metodo de mi objeto)
- Los objetvos que estan guardados como propiedades dentro del objeto 
- Los objetos que fueron recibidos como parametros del metodo
- Los objetos que fueron creados en el metodo

**Importante:** Eso no aplica si estamos hablado de data containers

Una buena forma de evitar esto (sobre todo el POO) es como en principio "Tell don't ask"

>  Procedural code gets information then makes decisions. Object-oriented code tells objects to do things.
-- Alec Sharp

Mirar esta link http://rubyblog.pro/2016/09/tell-dont-ask-principle

## SOLID Principles
SOLID son un conjunto de reglas que debemos asegurar en cumplir:
![[Pasted image 20221206105958.png]]

### Single responsibility principle (SRP)

> A class should have one and only one reason to change, meaning that a class should have only one job.

La forma mas facil de ver eso es porque motivo una clase podria cambiar. Si mesclo la generacion de un PDF con dar un PDF, eso esta mesclado el como genero un PDF a como lo presento, y eso viola SRP. 

### The Open-Closed principle (OCP)

> Objects or entities should be open for extension but closed for modification.

La idea es que en cierto punto una clase no deba ser modificada para añadir funcionalidad (la pensada) sino que se extienda. 

Esto nos permite asegurar que las clases pequeñas sigan siendo pequeñas y no hay codigo duplicado, osea que estemos DRY. 

### Liskov Substitution Principle

> Let q(x) be a property provable about objects of x of type T. Then q(y) should be provable for objects y of type S where S is a subtype of T.

En palabras simples: "The Liskov substitution principle simply implies that when an instance of a class is passed/extended to another class, the inheriting class should have a use case for all the properties and behavior of the inherited class."

### Interface segregation principle
> The interface segregation principle states that the interface of a program should be split in a way that the user/client would only have access to the necessary methods related to their needs.

O sea, no crear una interfaces de uso general, sino multiples interfaces. 

### Dependency Inversion principle (DIP)
Mirar aca:
https://www.digitalocean.com/community/conceptual-articles/s-o-l-i-d-the-first-five-principles-of-object-oriented-design
