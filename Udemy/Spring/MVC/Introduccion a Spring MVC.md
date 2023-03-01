- Utilizado para la creacion de aplicaciones web en java
- Basado en el Patron de diseño modelo-vista-controlador
- 
![[Pasted image 20230131095923.png]]

En la seccion de View template se puede utiliza tanto JSP como otros, por ejemplo FreeMarket o Velocity. 

Por lo tanto, una Spring MVC Application tiene 3 conjunto de elementos:
- UN conjunto de UI layout
- Una collecion de Spring Beans (que pueden ser controllers, services, etc)
- Spring configuration

Siguiendo el digrama de arriba, el `Front controller` ya esta desarrolado, y es parte del framework de spring. Tambien es conocido como el `Dispatcher Servlet`. Nuetro trabajo sera manejar el `Controler` , el `View template` y los `model` que conectan las 3 areas. 

## Roles 

### Controller 
Se encarga e la logica del programa, osea maneja el pedido, procesando y devolviendo lo pertinente y enviando la informacion adecuada al view template. 

### Model
Utilizado para almacenar la informacion. Tanto en sistemas como bases de datos, como para pasar la informacion a otra parte del sistema, como el view template. Se pueden utilizar Spring beans. 

### View template
Permite crear template para las paginas web. Los mas comunes con JSP + JSTL. Esta eleccion es muy flexible. 

