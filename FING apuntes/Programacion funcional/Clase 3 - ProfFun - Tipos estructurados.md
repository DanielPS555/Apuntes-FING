
## Tuplas
- Una tupla combina en un mismo objeto a un numero fijo de valores, cada uno con un tipo determinado. 
- Algunos ejemplos
	- (8, 23) :: (Int, Int)
	- ("Juan", 23, 60000) : (String, Int, Int)
- Se puede aplicar `patter matching`, ligando cada entrada con una variable
	```hs
	nombre :: (String, Int, Int)
	nombre (n , e , s) = n
	```
- Se puede ignorar componentes, utilizando `_` 
	```
	edad ( _ , e, _ ) = e
	sueldo ( _ , _ ,s) = s
	```

- Se pueden forzar valores haciando uso del patter martching
	```hs
	esPedro ("Pedro", _ , _ ) = True 
	esPedro ( _ , _ , _ ) = False
	```


### Sinonimos
A los tipos les podemos dar nombres. Por ejemplo 
``` hs
	type Coord = (Int, Int)
```


## Listas
Combina un mismo objeto con un numero arbitario de valores, pero todos del mismo tipo 
EJ: 
````
[82,3,1] :: [Int]
[("Juan",23,60000), ("Pedro", 44, 60000)] :: [Empleado]
````

Las listas se construyen inductivamente. Donde 
```
	valor : lista  
```

Agrega el elemento a la lista. Por ejemplo otra forma de crear la lista [1,2,3] es 
```
1:2:3:[] : [Int]
```

*Prelude* da un conjunto de funciones sobre listas. Algunas de ellas son: 
- ++
- !!
- length
- replicate
- take
- drop
- reverse
- etc

Tambien se puede aplicar *Pattern matching* sobre las listas, algo por ejemplo 
```
head (x : _) = x 
tail ( _ : xs) = xs
```


#### Lista por comprencion

![[Pasted image 20230305213608.png]]


Notar que podemos poner tantas fuentes de datos y filtros como querramos


## Tipos de datos algebraicos

Podemos definir 3 tipos de datos asi:
- *Enumerados*: 
	```
	data PuntoCardinal = Norte | Sur | Este | Oeste 
							deriving (Show, Eq)
	```
- *Productos*:
	```
	data Empleado = Empleado String Int Int 
						deriving (Show, Eq)
	```
	Aqui Empleado es un constructor. Mas para construir Empleados por ejemplo podria ser
	```
		pedro = Empleado ("Pedro", 50, 20000)
	```
- *Alternativas*:
	```
	data Forma = Circulo Float 
				| Rectangulo Float Float
				 deriving (Show, Eq)
	```

Un ejemplo de funcion con este tipo de datos: 
![[Pasted image 20230305220810.png]]
