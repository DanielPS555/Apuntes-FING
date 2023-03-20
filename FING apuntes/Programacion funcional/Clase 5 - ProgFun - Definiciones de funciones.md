
## Estructura de condicionales

![[Pasted image 20230319030228.png]]

## Pattern matching
![[Pasted image 20230319030306.png]]

La que es `var@pat` es que `var` hace referencia a toda la variable, asi no se tiene que volver a armar con el patron que se aplique luego de la @.

#### Ejemplos
![[Pasted image 20230319030412.png]]


## Definiciones locales (where / let)

Se puede utilizar la palabra reservada `where` de la siguiente forma: 

```
f x y = (a + 1) ∗ (b + 2) 
	where a = (x + y) / 2 
		  b = (x + y) / 3
```

Tambien se puede utilizar con estructura condicional. 

La otra opcion es con ``let`` 

```
	f x y = let a = (x + y) / 2 
			in (a + 1) ∗ (a + 2)
```

El alcanze de las variable definida en el `let` es lo que esta dentro del in. 
*Importante:* Si una variable que ya estaba declarada se declara en el let, entonces le piza el valor a la anterior. 

#### Ejemplos
![[Pasted image 20230319030832.png]]

## Operadores

Pueden tener la forma `infija` la cual seria por ejemplo 
```
	3 + 4
	7 * 8
```
Para poder usar estos se requiere que este saturado, osea que se tenga todos los parametros.

Se puede crear una `funcion prefija currificada` poniendo el operador entre parentesis. 
Osea 

```
	(+) 4 3
```

La ventaja que tiene esto es podemos `parametrizarlo parcialmente`. 
Por ejemplo `(+) 3` nos da una funcion que le suma 3 a cualquier parametro que le pasemos.

#### Secciones
> Las secciones son una sintaxis especial para expresar la parametrizaci´on parcial de un operador infijo.

La forma es la siguiente: 

```
(3+) 
(7∗) 
(2 <=) 
(∗4) 
(>0)
```

**Importante:** 
- Ojo con el orden, no tiene nada que ver la seccion `(5/)` que `(/5)`. 
- Notar que el parametro que falta en el operador es lo que le pasamos
- Se usa mucho para concatenar funciones con el operador "`.`"

Estos son muy utiles en operaciones que requieran una funcion como entrada. 


## Funciones anonimas
![[Pasted image 20230319031758.png]]

Osea, aca podemos definir una funcion y usarla en el lugar, algo muy util en un map por ejemplo. 

