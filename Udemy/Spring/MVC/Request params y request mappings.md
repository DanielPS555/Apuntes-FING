
## Request Params

Una forma de poder leer un parametro desde un formData es añadiendo añ metodo del 
controler un `HttpServletRequest` al cual se le puede ejecutar un `.getParameter("nombreParametro")`. 

Una forma mas simple es utilizado @RequestParam("nombreParametro"), el cual se lo añade a los parametros del metodo del controlador, esto hace que el valor buscado nos llege como parametro del metodo y no tengamos que solicitarlo al request del servlet. 

```java

@RequestMapping("/processFormv2")
public String letsShoutDude(
	@RequestParam("studenName") String name,
	Model model){

	....
}
```


Spring inyectara el valor del parametro studentName dentro del parametro name



## Request Mappings
Se utiliza para dar de una URL a un endpoint, se puede situar en dos lados: 
- En el `Controlador`: Esto define una URL base para todos los endpoint de ese controlador
- En el `End point`: Este define una URL para el metodo en si, va luego que el de la clase. Por lo que el formato termina siendo `/URL_CONTROLADOR/URL_ENDPONINT`.