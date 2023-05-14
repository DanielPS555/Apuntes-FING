
Supongamos que tenemos una funcion muy simular para diferentes tipos. 
Podriamos definir esta funcion por tantos tipos. O podriamos utilizar el *polimorfismo* + funciones de *alto orden*. 

Por ejemplo algo asi

```
elemGen :: (a → a → Bool) → a → [a] → Bool 
elemGen [ ] = False 
elemGen eq x (y : ys) = eq x y || elemGen eq x ys
```

Notemos que puede ser un poco dolor de huevos tener que pasarle la funcion ((a → a → Bool)) cada vez que llamamos a la funcion que tenga ese tipo y use ese comportamiento del tipo `a`. 

Entonces podemos usar una *type classe*
Por ejemplo podemos definir la clase *Eq* de la siguiente forma: 

```
class Eq a where 
	(==) :: a → a → Bool 
	(/=) :: a → a → Bool
```

Tambien podemos definir funciones por defecto dentro de la clase, con el fin de no tener que definirlas todas cuando se cree la instancia. Por ejemplo
```
class Eq a where 
	(==),(/=) :: a → a → Bool 
	x /= y = not (x == y) 
	x == y = not (x /= y)
```

Es por eso que solo hay alguna de las funciones en la implementacion

```haskel
data ConIgual = Mismo | Mismisimo 
instance Eq ConIgual where 
	Mismo == Mismo = True 
	Mismisimo == Mismisimo = True 
	_ == _ = False
```


Podemos usar *deriving* para automaticamente hacer que un dato propio sea instancia de una una clase conocida. Pero eso solo funciona en algunas clases 

```
	data ConIgual = Mismo | Mismisimo 
		deriving (Eq)
```

### Herencia
Se pueden crear clases las cuales dependen que sus tipos tambien dependan a otras clases. O sea un concepto de herencia. 

```
class Eq a ⇒ Ord a where 
	(<),(<=),(>),(>=) :: a → a → Bool 
	max, min :: a → a → a 
	compare :: a → a → Ordering 

data Ordering = LT | EQ | GT
```

Notar que en este caso, para definir `Ord` se requiere que la instancia tenga `Eq`. 

**Importante** para Ord. Para definir Ord por lo menos se tiene que dar una implementacion de *compare* o $\leq$.

### Restriciones de instancias
Notar que podemos dar una restriccion sobre instancias, donde definimos una instancia de un elemento bajo ciertas condiciones. 

Por ejemplo en el siguiente elemento damos una impementacion de Eq para las ruplas (a,b), pero se debe cumplir que tanto a como b sea instancia de Eq. 

```
instance (Eq a, Eq b) ⇒ Eq (a, b) where 
	(x, y) == (z,w) = x == z && y == w
```

### Algunas clases 

#### Enumerados
Esta clase comprende tipos como Bool, Char, Ordering, Int, Integer, Float, Double
	La clase Emun *requiere* de *Ord*

Algunos metodos son: 
- `succ`
- `pred`
- `toEnum` : `Int -> a` . Nos da el elemento el elemento de `a` que correponde a ese indice. Se usa generalmente con `:: tipo de a`. Ej `toEnum 90 :: Char`
- `fromEnum` : `a -> Int`
- `enumFrom`: `a -> [a]` Devuelve la lista de los enum luego del 1º parametro.
		Se puede abreviar como `[n ..]`
- `enumFromThen`: `a -> a -> [a]` Devuelve la lista de todos los elemento luego del 1º siguiendo la lista entre el 1º y el 2º
		Se puede abreviar como `[n, m ..]`
		Ej: `[1,3 ..]` =[1,3,5,7,9,.......]
- `enumFromTo`: `a -> a -> [a]` Analogo a `enumFrom` pero solo que el ultimo parametro da un limite superior. 
		Se puede abreviar como `[n .. m]`
- `enumFromThenTo`: `a -> a -> a -> [a]`Analogo a `enumFromThen` pero con un limite superior
		Se puede abreviar como `[n, m .. p]`

#### Numericos
```
	class Num a where
	 (+),(−),(∗) :: a → a → a 
	 negate :: a → a 
	 abs :: a → a 
	 signum :: a → a 
	 fromInteger :: Integer → a
```

Como minimo hay que implementar: 
	(+),(∗), abs,signum, fromInteger y negate o (−)

####  Show

```
	type ShowS = String → String 
	
	class Show a where 
		showsPrec :: Int → a → ShowS 
		show :: a → String 
		showList :: [a] → ShowS
```

Como minimo definir 
	show o showsPrec.

#### Read 

```
	type ReadS a = String → [(a, String)] 
	
	class Read a where 
		readsPrec :: Int → ReadS a 
		readList :: ReadS [a]
```

`read` es una funcion que esta definida como *top-level*  y utiliza a `readsPrec`. 

La forma de uso de read es: EJ:  ``read "2" :: Integer`