Se puede utilizar el Standar `ean Validation API`. Esta es soportada desde Spring 4. 
Esto es solo una espesificacion, se requiere de una implementacion, `Hibernate` implementa dicho estandas, de una forma independiente que el manejo de base de datos. 
Originalmente Hibernate era solamente un ORM project, ha ido evolucionando, esto es parte de su evolucion. 


Los tipos de validaciones que hay son: 
- Required 
- Validate length
- validate numbers 
- validate with regular expressions
- custom validation

## Algunas anotaciones

- `@NotNull`: Verifica que el valor no sea null. 
- `@Max`: Da una cota superior al numero
- `@Min`Da una cota inferior al numero
- `@Size`: Espesifica el tamaño que se espera 
- `@Pattern`: Verifica que la exprecion regular se cumpla
- `@Future`: Verifica que la fecha sea futura a una fecha dada
- `@Past` Verifica que la fecha sea pasada a una fecha dada

Para correr la vaidacion, lo que podemos hacer es que en el endpoint añadimos a la clase a validad la etiqueta `@Valid`.
Tambien podemos pedir el parametro de tipo `BindingResult` para poder el resultado de la validacion. 

```java

@RequestMapping("/processForm")
public String processForm(
		@Valid @ModelAttribute("customer") Customer theCustomer,
		BindingResult theBindingResult){

	if(theBIndingresult.hasErrors()){
		return "customer-form"
	}else{
		return "customer-confirmation"
	}

}



```