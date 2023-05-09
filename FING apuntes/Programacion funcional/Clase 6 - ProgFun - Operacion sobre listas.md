## Constructores de lista 
Hay dos constructores

```
	[] :: [a]
```

```
	(:) :: a -> a -> [a]
```

El segundo constructor asocia a la derecha. 

## Generador de lisas 

La expresion `[m .. n]` denota la lista de valores entre m y n. 

#### Ejemplo interesante 
Notar que una funcion se puede escribir en su forma *infija como*
```
	m `divide` n = n `mod` m == 0
```

Si la usamos de esta forma, podemos utilizar esta forma como una *seccion*, por ejemplo.

```
divisores n = filter (`divide` n) [1..n]
```


## Operador $

La idea de este *operadore de aplicacion* es dar un operador de *baja prioridad* con el fin de evitar parentesis. 
Este operador tiene prioridad 0 (super baja)

Y nos permite hacer cosas como esta 

```
	succ . succ $ 3 * 4

	Sino tenia que ser 

	(succ.succ)(3*4)

```

## Diseño composicional
Son funciones escritas unicamente en base a composiciones de otras. Un ejemplo es una forma de escritura de la funcion *trail*. 

## Funciones de listas importantes 

#### take 
Sintaxis: `take n xs` 

Retorna los primeros `n` elementos de xs

#### drop 
Sintaxis: `drop n xs`

Retorna la lista `xs` sin los primeros `n` elementos. 

Notar que 
```
take n xs ++ drop x xs = xs 
```

#### last
Sintaxis `last :: [a] -> a`

Retorna el ultimo elemento de la lista. 
Una forma de escribirla puede ser 

```
	last xs = head $ drop (length xs - 1) xs
```

#### splitAt
Sintaxis: `splitAt :: Int -> [a] -> ([a],[a])`

Divide la lista en dos, segun la posicion del 1º parametro. 
Una forma de escribirla es: 
```
splitAt n xs = (take n xs, drop n xs)
```

#### trail
Sintaxis: `trail:: int -> String -> String`

Nos devuelve las ultimas n lineas (siendo n el primer parametro)

```
	trail n = unlines . reverse . take n . reverse . lines
```

#### takeWhile
Sintaxis: `takeWhile :: (a -> Bool) -> [a] -> [a]`

Esta funcion retorna todos los elementos de la lista hasta que uno de ellos no cumple la condicion

#### dropWhile
Sintaxis: `dropWhile :: (a -> Bool) -> [a] -> [a]`

Esta funcion elimina de la lista todos los elementos hasta que uno de ellos no cumple la condicion.

#### zip
Sintaxis: `zip :: [a] -> [b] -> [(a,b)]`

Devuelbe los pares de loa 1º elementos de a y b, los 2º elementos de a y b, y asi continua
EJ `zip [1,2,3] [a,b,c,d] = [(1,a),(2,b),(3,c)]`

##### Algunos ejemeplos interesantes
```
	productoEscalar :: Num a => [a] -> [a] -> a
	productoEscalar xs xl = sum . map ( uncurry(*) ) $ zip xs xl
```

```
	listaDecendente :: Ord a => [a] -> Bool
	listaDecendente xs =  and . map (uncurry (<)) $ zip xs (tail xs)
```

#### zipWith
Sintaxis `zipWith :: (a -> b - > c) -> [a] -> [b] -> [c]`

La idea es aplicar una funcion a las parejas del 1º elemento, 2º elemento ... de los conjunto `a` y `b`. 

Una forma de escribirlo es: 

```
	zipWith f la lb = map (uncurry f) (zip la lb)
```

#### foldr
Sintaxis `foldr :: (a -> b -> b) -> b -> [a] -> b`

La forma de esta funcion es la siguiente: 
Sea: 

```
	foldr f e [x1, ... , xn]

	foldr f e (x1 : x2 : ... : xn : [])

	Analogo a: 
	f x1 (f x2 (...(f xn e)...))
```

##### Ejemplos interesantes 
```
sum :: Num a ⇒ [a] → a 
sum = foldr (+) 0

and :: [Bool ] → Bool 
and = foldr (&&) True


map :: (a → b) → [a] → [b] 
map f = foldr fcons [] 
	where fcons x r = f x : r


filter :: (a → Bool) → [a] → [a] 
filter p = foldr op [ ] 
	where op a r | p a = a : r 
				 | otherwise = r

```