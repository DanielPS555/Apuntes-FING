
- En PF consiste en esencialmente una lista de *definiciones*
- Las definciones son escritas como *ecuaciones. Se puede acompañar de su tipo 

 Ej:
```hs
	num :: Integer
	num = 3 + 6
```
 

Se puede omitir el tipo, se auto infiere 

Para defunir funciones, espesificamos sus *parametros formales*

```hs
	square :: Integer -> Integer
	squeare x = x * x
```


Usar Tipado es algo bueno, ayuda a encontrar problemas y es parte de la espesificacion del sistema. 

## Tipado
- Haskell tiene tipado fuerte. Ya que todas las constantes, variables  operationes tiene un tipo asociado. 
- Se hace unn chequeo de tipos en tiempo de compilacion
- *Type sagfety*: Los programas bien tipados, nuca tiene un problemas debido al tipado en tiempo de ejecuccion.

## Tipos basicos: 
- Bool = Posibles valores True, False (con mayusculas)
- Char
- String
- Int (enteros acotados)
- Integer (Enteros no acotados)
- Float 
- Double

### Boolean
#### Operaciones priimitivas
Son las abituales: 
- not
- && 
- ||

### Enteros
- Hay dos tipos Int (acotados) Integer (no acotados)
- Los operadores basicos son (para ambos tipos): 
	- +
	- -
	- *
	- ^
	- div
	- mod
	- abs
	- negate
	Atencion: Todos  tiene que que tomar dos integer o dos int
- Pueden ser comparados: 
	- ==
	- /=
	- >
	- <
	- >=
	- <=
- Para pasar de Int a Integer o Integer a int hay que hacer conversion explicita:
	- fromInteger :: Integer -> Int
	- toInteger :: Int -> Integer

### Caracteres
- Se escriben con comillas simples 
- Algunos caracteres especiales: 
	- \\t tab
	- \\n newLine
- La conversion entre un caracter y su condificiacion se hace los con siguientes funciones
	 - FromEnum :: Char -> Int
	 - ToEnum :: Int -> Char
### Reales
- Hay dos tipos de reales de punto flotante.
- Las operaciones son las estandar (arismeticas, trigonometricas, etc)
- Se añade la operacion de divicion real : /
- Hay funciones de conversion: 
	![[Pasted image 20230305163142.png]]
	

### String 
- Se definen como una lista de caracteres
- Constante de tipo String va entre commilas dobles
- Hay funciones de conversion: 
	- show (4+3) => "7"
	- read "3" + 4 => 7


## Operaciones con multiples parametros
Se ponen los tipos de parametros en entradas concatenados por flecha, el ultimo de la cadena es el tipo del output

EJ: 
```hs
	exor :: Bool -> Bool -> Bool
	exor x y = (x||y) && not (x && y)
```

## Pattern Matching

Aqui la funcion tiene multiples entradas, donde si la funcion tiene n variables, se evalua de arriba hacia abajo hasta encontrar una que cumpla el valor, luego se ejecuta la ecuacion de ese patron 

```hs
exOr :: Bool -> Bool -> Bool
exOr True y = not y
exOr False y = y
```