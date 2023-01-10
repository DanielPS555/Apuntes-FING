 Hay dos aspectos que hay que tener cuidado
 - Trabajar con funciones que sean faciles y legibles. Aca importa mucho el tamaño del cuerpo de la funcion.
 - La llamada de las funciones tambien tiene que ser legible. Aca importa mucho el nombre, el numero de parametros y su orden. 

## Parametros
*Idea principal:* La idea es intentar minimizar el numero de parametros:
- `Ningun parametro`: La mejor opcion
- `Un parametro`: Muy buena opcion
- `Dos parametros`: Baja lo intuitivo, igual es aceptable
- `Tres parametros`: Intentar evitar si es posible 
- `Mas parametros` Intentar evitar a toda costa porque ya se vuelve bastante diificil de llamar

### Algunas cosas importantes
- Pasar objetos terminados en vez de los elementos que lo confirman. EJ: Si un usuario tiene nombre e email, no pasar a una funcion el nombre y el email si le podes pasar el usuario. 
- No es un problema que una funcion tenga 2 metodos si son claros que deben ser y el orden, por ejemplo una funcion `add`.
- Eviar usar `parametros de salida` . Y si lo vas a hace poner un nombre que lo deje claro. 

### Algunas buenas buenas formas de reducir el numero de atributos
- Si tenemos muchos parametros, para evitar el problema del orden se pueden pasar por parametro un JSON , o un MAP


## Cuerpo de las funciones
*Idea principal: son* 
- La idea es que las funciones sean chicas
- Las funciones tiene que hacer solo una cosa

Por lo tanto:
- La idea es que en un mismo metodos no se mesclen codigo con alto nivel de abstracion y codigo con bajo nivel de abstracion
- No repetir codigo, osea mantener el codigo DRY. Sino si queremos cambiar algo lo tenemos que cambiar de varios lados

Reglas basicas :
- Extraer codigo que tiene la misma funcionalidad. Osea juntar todo eso en una misma funcionalidad
![[Pasted image 20221202144011.png]]

- Extraer codigo que requiera mas interpretacion que el codigo que lo rodea
![[Pasted image 20221202144027.png]]


No debemos dividir una funcion si: 
- Estamos simplemente renombrado la operacion
- Si encontrar esta nueva funcion lleva mas tiempo que leer el codigo que se extrago. 
- No se puede encontrar un nombre para esta funcion que no choque con el nombre original de la funcion de donde se lo extrae

### Funciones puras
Se debe intentar que las funciones sean puras. 
Una funcion es pura si:
- Para los mismos parametros de entrada, la salida es la misma
- No tiene `side effect`. 

#### side effects
Un side effect es una operacion que no solamente actua sobre los parametros de entrada, y cambia los de salida. Sino que *cambia el estado general del sistema*. 

El problema con los side effects es cuando lo hace una funcion y para quien la usa es **Inesperada**. 

Entonces si tenemos en una funcion un side effect, tenemos que hacer una de las dos siguientes cosas: 
- Escoger un nuevo nombre para la funcion que signifique lo que hace
- Mover el side effect a otra funcion o lugar

Un indicador que una funcion debe ser separada, es que si queremos testar una funcionalidad, si probar esta funcionalidad es facil o no. Porque si la misma esta metida dentro de una funcion muy compleja, capaz identificamos una funcion a dividir