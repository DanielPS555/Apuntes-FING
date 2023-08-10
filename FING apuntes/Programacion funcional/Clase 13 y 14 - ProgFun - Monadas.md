Las *monedas son* utilizadas para el modelado de *efectos computacionales*. En otras palabras, efectos los cuales no le queremos dar bola, pero si estan ahi y deben ser atentidos. 
Algunos ejemplos son:
- Entrada y salida
- Estado
- No determinismo 
- Fallas 
- Excepciones



## Para fallas

- Algo muy usado es em *Maybe* para el manejo de fallas 

- Por ejemplo si tenemos la *eval* en el tipo *Exp* definido asi: 
```
data Exp = Num Int | Add Exp Exp | Div Exp Exp
```

Entonces para el manejo de la div por cero, tenemos que hacer que *eval* sea 
```
	eval :: Exp -> Maybe Int
```

Al introducir el Maybe, se introducern un monton de manejo de los Nothing que añade un  monton de temas al pedo: 

```
eval :: Exp → Maybe Int 
eval (Num n) = Just n 
eval (Add x y) = case eval x of 
					Nothing → Nothing 
					Just a → case eval y of 
						Nothing → Nothing 
						Just b → Just (a + b) 
eval (Div x y) = case eval x of 
					Nothing → Nothing 
					Just a → case eval y of 
						Nothing → Nothing 
						Just b → a ‘divM‘ b
```


Aqui se define el operador *bind* (>>=) y el *return* con la siguiente forma: 

```
return :: a → Maybe a 
return a = Just a

(>>=) :: Maybe a → (a → Maybe b) → Maybe b 
m >>= f = case m of 
			Nothing → Nothing 
			Just a → f a
```

Utilizando la notacion anterior nos queda: 

```
eval :: Exp → Maybe Int 
eval (Num n) = return n 
eval (Add x y) = eval x >>= λa → eval y >>= λb → return (a + b) 
eval (Div x y) = eval x >>= λa → eval y >>= λb → a ‘divM‘ b
```



## Clase Monad

```
class Monad m where
	(>>=) :: m a → (a → m b) → m b 
	(>>) :: m a → m b → m b 
	return :: a → m a 
	fail :: String → m a 
	
	m >> k = m >>= λ_ → k 
	fail s = error s
```


## Notacion do-notation utilizando monadas
![[Pasted image 20230617182906.png]]


## Algunas funciones utiles

#### liftM2
```
liftM2 :: Monad m ⇒ (a → b → c) → m a → m b → m c 
liftM2 f m m' = do  x ← m 
			     	y ← m' 
					return (f x y)
```

#### sequence
Evalua las Monad en secuencia y devuelve un array de los resultados de cada Monad
```
	sequence :: Monad m ⇒ [m a] → m [a] 
	sequence [ ] = return [ ] 
	sequence (m : ms) = do  x ← m 
							xs ← sequence ms 
							return (x : xs)
```

#### filterM
```
filterM :: Monad m ⇒ (a → m Bool) → [a] → m [a] 
filterM [ ] = return [ ] 
filterM p (x : xs) = do b ← p x 
						ys ← filterM p xs 
						return (if b then x : ys else ys)
```


#### mapM


#### foldM



## Monada de estado
Esto es una monada en la que se manteiene por debajo un estado, y estado se actualiza luego de la ejecucion de cada monada 
