# Optimos globales y locales 
## Indice
- Objetivos: 
	- Vocabulario
	- Estudiar caracteristicas e soluciones optimas 
	- Aprender el metodo para determinar soluciones optimas
- Definiciones, condicion necesari y suficiente 
- Condicion de KKT

## Definiciones
Tenemos un probema general de optimizacion 
[nota 1]
y de programacion matematica
[nota 2]

*Importnate:* Los problemas de optimizacion general no tiene restricciones, por ende el dominio es toda la region factible. 


#### Optimo global
$x' \in F$ es un optimo global de G si $f(x') \leq f(x) , \forall x \in F$. Notar que porque los problemas de los que partimos es minimizar, si fuera maximixar buscamos el $f(x') \geq f(x) \forall x \in F$ .  

#### Optimo local
$x' \in F$ es un optimo local de G si $\exists \epsilon > 0 : f(x') \leq f(x) \forall x \in F$ con $|| x - x' || < \epsilon$ 

[nota 3]

#### Dirrecion factible
`d` es una *dirrecion factible* de G en $x' \in F$ si:
[nota 4]

*obs:* Si $x'$ es interno de F $\Rightarrow$ Todas las dirrecion son factibles 

#### Dirrecion de decenso (puede ser de asenso en el caso opuesto)
`d` es una dirrecion de desenso de `f` en $x'$ si $f(x' + \zeta d) < f(x')$ .

Osea si luego de dar un paso infinitesinalmente pequeño desendi, entonoces es una dirrecion de desenso. 


## Teoremas

#### Teorema 1
Sea `f` diferenciable en $x'$ 
[nota 5]


#### Teorema 2 (condicion necesaria para un optimo local)
Si $x'$ es un optimo local 
$\Rightarrow$ no existe una dirrecion factible y de desenso al mismo tiempo en $x'$.

#### Teorema 3
Sea $x'$ diferenciable en $x'$.
$x'$ optimo local 
[nota 6]


[nota 7]



#### Teorema 
Sean `f` y `F` conexas
Un optimo global $x'$ no puede existir una dirrecion que sea factible y de desenco al mismo tiempo. 

*obs*: Estamos diciendo que sea convexo





## Condicion de KKT (Karush kuhn kuker)
Aqui las condiciones son:
	$min f(x)$
	sa
		$g(x) \leq 0$
		$x \in X$



Super importane: Si F y f son convexas, la condicion necesaria de optimo global se conviete en syfuciente 