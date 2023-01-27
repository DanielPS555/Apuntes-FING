Se puede utilizar en remplazo de la configuracion del `Spring Container` utilizado `Java code` . 

## ¿Como crearlo?
Comenzaremos creando una clase en java con la anotacion `@Configuration`. Opcionalmente se le puede añadir soporte por escaneo con `@ComponentScan`. 

Estos dos pasos se pueden hacer de la siguiente forma: 

```java

@Configuration
@ComponentScan("DIRECTORIO A ANALIZAR")
public class SportConfig{
	.....
}

```

Luego podremos conseguir un conexto (para obtener bean por ejemplo) con lo siguiente: 

```java
AnnotationConfigApplicationContext context = new AnnotationConfigApplicationContext(SportConfig.class);
```

Luego la obtencion de Bean es igual que con la configuracion XML. 

## Crear Bean desde la configuracion
Se pueden crear exponiendo metodos que los crean 
```java
@Configuration
public class SportConfig {

	@Bean
	public Coach swimCoach(){
		SwimCoach mySwimCoach = new SwimCoach();
		return mySwimCoach;
	}

}

```

Notar que el Id de este bean es `swimCoach`, osea el nombre del metodo. 

Luego para la inyecion de dependencias se hace de la siguiente forma: 

```java
@Configuration
public class SportConfig {

	@Bean
	public FortuneService happyFortuneService(){
		return new HappyFortuneService();
	}

	@Bean
	public Coach swimCoach(){
		SwimCoach mySwimCoach = new SwimCoach(happyFortuneService());
		return mySwimCoach;
	}

}

```

## Utilizar property file

Para cargar un propery file se utiliza la etiqueta `@PropertySource(classPath:sport.properties)`. Luego para leer esos valores se procede con la anotacion `@Value`

```java

public class SwimCoach implements Coach{

	@Value("${foo.email}")
	private String email;

	@Value("${foo.team}")
	private String team;

}

```