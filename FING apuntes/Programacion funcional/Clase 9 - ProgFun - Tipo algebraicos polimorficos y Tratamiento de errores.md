
# Tipo algebraico polimorfico
Ya habiamos visto como formar *Tipos algebraicos*, incluso los recursivos. 

Ahora, si queremos definir un tipo de dato algebraico, pero para un tipo de dato albitrario (por ejemplo arboles con el tipo Int o Bool o cual sea dentro) ¿como hacemos?

Bueno, la solucion son los *tipos algebraicos polimorficos*. Estos se declaran asi: 

```haskel
	data T a1 .. am = C1 t_1_1 ... t_1_k1

					  Cn t_n_1 ... t_n_kn	
```

Donde los a1 ... am pueden contener *variables de tipo*, estas variable pueden ser usadas en los constructores de ese tipo. 

Ejemplo:
```haskel
	data Pair a b = Pair a b
```

Para hacer referencia al tipo lo hacemos como (`Valor variables de tipo`)

Por ejemplo 

```
	data List a = Nill | Const a (List a)
```

**Importante**: No se puede dejar "libre" una variable de tipo en la definicoon de un tipo algebraico. O sea, que si uso una variable `b` en los constructores, tiene que estar en las variables de tipo.


## Definir funciones

Hay tres forma de definir funciones en relacion a los tipos algebraicos polimorficos

#### Funciones polimorficas 
Aqui el tipo de la funcion es libre 
Ej: 
```haskel
	length :: List a → Int 
	length Nil = 0 
	length (Cons xs) = 1 + length xs
```

#### Funciones con polimorfismo ad-hoc
Aqui el tipo de las funciones esta restringido con el uso de una clase, pero igualmente sigue siendo libre. 
Ej
```haskel
	maximum :: Ord a ⇒ List a → Int 
	maximum (Cons x Nil) = x 
	maximum (Cons x xs) = max x (maximum xs)
```

#### Funciones no polimorficas
Aqui el tipo polimorfico esta defindio. Por ejemplo a un char o otro tipo
Ej
```haskel
	sumOrd :: List Char → Int 
	sumOrd Nil = 0 
	sumOrd (Cons x xs) = ord x + sumOrd xs
```

# Manejo de Errores

Haskel no da un soporte para el manejo de errores por ser un lenguaje funcional puro. 

Hay algunas tecnicas que podemos utilizar de todas forma: 

#### Funcion parcial 
En la funcion tenemos un conjunto de condicionales, solo se procesa la valida

```
myDiv1 :: Int → Int → Int 
myDiv1 x y | y /= 0 = div x y
```

#### Utilizar la funcion error
La funcion error se define como `error :: String -> a`
```haskel
myDiv2 :: Int → Int → Int 
myDiv2 x y  | y /= 0 = div x y 
	     	| otherwise = error "Division por cero"
```

#### Utilizar un valor dummy
Ese valor puede ser elegido (como en el ejemplo es 0) o se lo puede solicitar por parametro.
```haskel
myDiv3 :: Int → Int → Int 
myDiv3 x y  | y /= 0 = div x y 
			| otherwise = 0
```


### Uso del Maybe y Either

Podemos usar el tipo ``Maybe`` para el manejo de errores, en el cual una funcion devuelve `Nothing` si es un error y `Just VALOR` si el resultado el correcto. 

El tipo seria 
```haskel 
data Maybe a = Nothing | Just a
```

Un ejemplo seria: 
```
	myDiv5 :: Int → Int → Maybe Int 
	myDiv5 x y | y /= 0 = Just (div x y) 
			   | otherwise = Nothing
```

Notar que si una funcion llama a algo que le retorne Maybe tiene que considerar a parte el caso de Nothing

El problema con eso es que no podemos retornar el motivo del error. Pero con `Either` podemos hacer esto o devuler cualquier cosa que queramos (como un valor dummy) en el `Left`.

```haskel
data Either a b = Left a | Right b
```

Un ejemplo: 
```haskel 
myDiv6 :: Int → Int → Either String Int 
myDiv6 x y | y /= 0 = Right (div x y)
		   | otherwise = Left "Division por Cero"
```
