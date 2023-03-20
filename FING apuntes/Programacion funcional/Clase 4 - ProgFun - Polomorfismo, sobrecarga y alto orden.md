
## Polimorfismo parametrico

> El polimorfismo param´etrico es un mecanismo de tipado que permite definir funciones y tipos de datos de forma param´etrica de forma tal que puedan manipular valores de distintos tipos de forma totalmente uniforme.

Ejempos: 

``` hs
head (x : xs) = x 

head [1, 2, 3, 4] --> 1 

head [False,True, False] --> False 

head [’a’, ’b’, ’c’, ’d’] --> ’a’
```

El tipo inferido por haskel es:

```
	head :: [a] -> a
```

Lo anterior es el *tipo mas general* de head. Haskel tiene la capacidad de inferir el tipo mas general de una funcion.
A la variable a se la llama una *variable de tipo*. 

#### Algunas funciones polimorficas sobre listas:
(Todas en la libreria *Prelude*)
![[Pasted image 20230318203437.png]]


## Sobrecarga

Se puede utilizar el mismo operadores para definir funcionamientos diferentes segun el tipo de la funcion. 
Para esto se definen *clases*. 

Por ejemplo 

```
(==) :: EQ a => a -> a -> Bool
```

Aqui esta funcion esta definida para los tipos `a` tal que tiene implementada la clase Eq

Una clase por ejemplo podria ser 

```
class Eq a where 
	(==) :: a → a → Bool 
	(/=) :: a → a → Bool 
	x /= y = not (x == y) 
	x == y = not (x /= y)
```

Tambien podria definir asi: 
```hs
-- Location, in two dimensions.
	class Located a where
    getLocation :: a -> (Int, Int)
```

Luego para hacer que un tipo sea miembro de una clase en particular hay que definir una *instancia*

```
data T = A | B 
instance Eq T where 
A == A = True 
B == B = True 
_ == _ = False
```

Para algunas clases, ej Eq, Ord, Show, Haskel puede derivar automaticamente una instancia usando *deriving*.

```
data T = A | B 
	deriving (Eq, Show)
```

## Alto orden
En haskel, se llama funciones de alto orden a las funciones que toman una funcion como parametro o retornan una funcion como resultado. 

En programacion funcional las funciones son *cuidadas de primera clase*. Ya que se utilizan como elementos comunes. 

En las funciones con mas de un parametro, notemos que los parametros que se ponen como tipo1-> tipo2 -> tipo3 ... se puede ver como tipo1 -> (tipo2->tipo 3)). Osea que con pasarle el 1º tipo, nos devuelve una funcion que espera un solo parametro (lo que seria el 2º parametro de entrada de la funcion mirada de forma original)

Por ejemplo, a la funcion `take` se la puede ver de dos formas: 

```
take :: Int → [a] → [a]

o 

take :: Int → ([a] → [a])
```

Esto es porque el operador `->` *asocia a la derecha*

Cuando las funciones tiene esta forma (los parametros separados por ->) vemos que en realidad se trata de un conjunto de funciones que se van tomando de a 1 parametro, y se van generando nuevas. 
A este tipo de funciones se les dice que tiene la forma *currificada*

Por ejemplo `take 3` genera una funcion de tipo `[a] -> [a]`

Notemos que la asociacion de la evaluacion de las funciones es *asociada a la isquierda*. Por lo tanto es lo mismo: 
```
(take 3) [’a’, ’b’, ’c’, ’d’, ’e’]

y 

take 3 [’a’, ’b’, ’c’, ’d’, ’e’]
```

Por otro lado las operaciones *no currificada* toma los parametros en formas de tupla.

![[Pasted image 20230318223032.png]]

Un ejemplo de currificacion podria ser el siguiente: 

```
map (addc 1) [1,2,3]
```

Exite la operacion *curry* y *uncurry* las cuales permite pasar funciones currificadas a no currificadas y viseversa 

```
curry :: ((a, b) → c) → (a → b → c) 
curry f x y = f (x, y) 

uncurry :: (a → b → c) → ((a, b) → c) 
uncurry f (x, y) = f x y
```

Algunos ejemplos de caso de uso de curry uncurry podrian ser: 

```hs
-- Ejemplo con curry
map (addc 1) [1,2,3]
map (curry add 1) [1,2,3]
```

```hs 
-- Ejemplo con uncurry
zipWith' :: (a -> b -> c) -> [a] -> [b] -> [c]
zipWith' f xs ys = map (uncurry f) (zip xs ys)
```