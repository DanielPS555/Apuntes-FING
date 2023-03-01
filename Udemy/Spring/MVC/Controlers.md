Para poder crear ua clase que sea el controlador, lo que hacemos es añadir la etiqueta @Controller sobre la declaracion de la clase. 

```java
@Controller 
public class HomeController {
	....
}
```

Dato: 
- @Controler hereda de @Component

Luego podemos añadir metoods al controlador, los cuales para estar expuestos en la web lo que se hace es añadir la anotacion `@RequestMapping("URL")`, se puede profundizar sobre @RequestMapping en [[Request params y request mappings]]. 

```java
@Controller 
public class HomeController {

	@RequestMapping("/")
	public String showMyPage(){
		return "main-page"
	}

}
```

Si obervamos el archivo de configuracion `spring-mvc-demo-servlet.xml` podemos notar la seccion  

```xml 
<bean  
   class="org.springframework.web.servlet.view.InternalResourceViewResolver">  
   <property name="prefix" value="/WEB-INF/view/" />  
   <property name="suffix" value=".jsp" />  
</bean>
```

Esto lo que va a hacer es tomar el string devuelto, osea "main-page" y va a concatenarlo con : /WEB-INF/view/main-page.jsp, dando acceso a view que queremos devolver. 


Luego podemos crear la pagina  /WEB-INF/view/main-page.jsp con algo muy simple:

```html
	<html><body>
		<h2>HOla</h2>
	</body></html>

```



## Usando el Model

Podemos usar un `Model` para pasar extra informacion al JSP por ejemplo. Para ello se puede añadir un `Model` al parametro del metodo del Controlador.

Luego para poder utilizarlo se llama directamente con `${nombre del atributo}`  en el JSP