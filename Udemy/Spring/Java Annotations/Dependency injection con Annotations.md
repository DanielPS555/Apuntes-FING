
## Que es AutoWiring

Spring puede utilizar autowiring para la inyeccion de dependencias. Para ello Spring busca un bean que se corresponda por tipo, osea por clase o por interface. 

Para ello Spring escanea todos los @Components, luego busca algun bean que implemente el tipo pedido y lo inyecta. 

Hay 3 tipos de inyecciones autowiring:
- Constructor injection
- Setter Injection
- Field Injection

### Inyeccion por constructor

Aqui creamos el constructor con las dependencias necesarias, y luego con un @Autowired Spring se encarga de unir las dependencias. 

Ejemplo: 

```java

public class TennisCoach implements Coach{

	private FortuneService fortuneService;

	@Autowired
	public TennisCoach(FortuneService theFortuneService){
		fortuneService = theFortuneService;
	
	}

}

```


### Inyeccion por setter 
En estos casos el @Autowired se pone sobre el setter al cual se le debe inyectar. 

### Inyeccion por field
Tambien podemos poner un @Autowired sobre el atributo, esto funciona incluso con atributos privados. Para instanciar el valor, una reflexion, no los setter, por lo que no es necesario. 

## Method injection
Podemos inyectar dependencias en cualquier metodo, utlizado @Autowired. Por ejemplo: 

```java

@Autowired 
public void doSomeCrazyStuff(FortuneService theFortuneService){
	....
}

```

Esto va a inyectar automaticamente al FortuneService en el metodo. Este metodo se va a ejecutar al inicio, *por lo que en realidad es un metodo utilizado para la inyeccion de dependencias, no para un propocito general.*

## Qualifiers
Se utiliza con el fin de espesificar cual es el bean que debe elegir autowired, ya que hay multiples opciones basados unicamente en el tipo. 

Se puede usar en cualquier lado que este el @Autowired

Ejemplo 
```java

@Component
public class TennisCoach implement Coach{

	@Autowired
	@Qualifier("happyFortuneService")
	private FortuneService fortuneService;

}

```

Si es un constructor, el @Qualifier debe ir antes del metodo, no arriba del constructor. Y si es un setter puede ir tanto arriba del metodo como adelante del parametro. 

Un ejemplo de un constructor 

```java
@Autowired  
public TennisCoach(@Qualifier("randomFortuneService") FortuneService theFortuneService) {
   
        fortuneService = theFortuneService;  
}
    ```



## Inyectar propiedades por archivo 

Para ello, ensima del Field se usa la etiqueta  @Value("${NOMBRE_PROPIEDAD_PROPOERTY_PLACE_HOLDER}")

Un ejemplo 
```java
1.  @Value("${foo.email}")
2.  private String email;

4.  @Value("${foo.team}")
5.  private String team;
6. ```
Donde foo.email y foo.team estan declaradas en un archivo de tipo .property