
Son `marcadores especiales` el cual nos provee de `metdadata` de la clase.

Por ejemplo una anotacion muy usada es `@Override` 


Por lo general se utiliza anotaciones en vez de configuracion XML, ya que los xml pueden tener demaciada informacion. De esta forma XML minimiza la configuracion por XML. 

Spring lko que va a a hacer es analizar cada una de las clases en busqueda de anotaciones especiales, y luego va a configurar los Spring containers de forma.

Debemos dentro de las etiquetas `beans` declarar un scaner. Esti se hace de la siguiente forma: 

```xml

<beans>
	<context:component-scan base-package="PAQUETE A ANALIZAR DE FORMA RECURSIVA"/>

</beans>

```

Luego las clases que queramos que sean beans deben llevar la etiqueta `@Component` 

```java
@Component("idBean")
public class TennisCoach implement Coach{
	....
}

```

Podemos no espesificar un nombre en el @Component, para ello el id que automaticamente sera establesido por spring sera el nombre de la clase, comenzado por minuscula. En el ejemplo anterior deberia ser tennisCoach. 
Hay una excepcion, si el nombre comienza con dos mayusculas, el nombre del bean no cambia. 

Si una anotacion no tiene parametroos, no tiene porque llevar los parentesis al final. 
