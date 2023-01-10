El primer enfoque es evitar el *Deep nesting*. Para ello se usara:
- *Fabrica de funciones*
- *Utilizar errores*
Tambein intentaremos utilizar *Positive checks*


## Tecnica de Guards & Facil Fast

![[Pasted image 20221205104418.png]]

## Usar errores 
La regla es simple: Si algo es un error, hacer que sea un error usando el mecanismo de error de lenguaje de programacion. 

**Importante**: Manejar errores es considerado una cosa. Esto aplicado a que las funciones solo hagan una cosa. 
Osea que si iteramos, hacemos una accion y luego manejamos las exepciones en la llamada de la funcion, no seria clean code. Lo ideal en ese caso seria menajrlo dentro de la funcion, porque sino hariamos dos cosas, iterar y manejar el error. 