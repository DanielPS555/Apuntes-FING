Para espesificar el `Scope` de un Bean, debajo de la anotacion `@Componnet` se pone `@Scope("tipo de life cycle")`. 

Por ejemplo 

```java

@Component
@Scope("prototype")
public class TennisCoach implement Coach {
....
}
```


### Metodo de inicializacion
Situamos la etiqueta `@PostConstruct` ensima del metodo inicializador. De esta forma de ejecutara luego que el bean haya sido construido.


### Metodo de destruccion
Situamos la etiqueta `@PreDestroy` ensima del metodo que se debe ejecutar previo a que el bean sea destruido. 

*Importante:* Ninguno de los dos metodos puede recivir parametros. 