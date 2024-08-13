
## Algunas cosas previas

1. Recordar Lagrange 
	Queriamos resolver 
	$min·$  $f(x)$ con $h(x) = 0$ .
	
	Lo cual se cumple que el conjunto que cumple que $h(x) = 0$ recubre un conjunto, y la solución sera el borde de esta. 
	Por lo tanto terminamos con una solución donde el gradiente de $h$ y $f$ terminan siendo colineales, o sea: $\nabla f(x) + \delta \nabla h(x) = 0$.


2. A la funcion de costo se le puede "añadir un peso" segun que tan grande sea la norma de $x$. Por ejemplo se podria formular:
	$$||Ax - b||_2^2 + \delta ||x||_2^2$$
	Donde mientas mas grande sea $\delta$ mas peso tiene la norma de $x$ en la función de costo. 
	
	```ad-seealso
	La anterior forma tiene varios nombres segun el dominio, por ejemplo "Ridpe representaion"
	```

3. "Sobre la dureza de las restricciones"
	El problema es que si ponemos una restricciones de la forma $f(x) < 0$, entonces perdemos persepcion que tan buena es una $x$, porque para esa restricciones es igual de mala $x = 0.0001$ como $x=10000$. O sea, no tenemos nocion de que tan malo o que tan bueno es un valor. 


## Teoria de Lagrange y Dualidad
Esto es solo un pantallazo. 

Tomemos un problema en su forma estandar, que vamos a llamar `problema primal`. 

Esto es: 

$min$ $f_0(x)$ 
Sta: $f_i(x) \leq 0$ con $i=1..m$ 
    $b_j(x) = 0$  con $j = 1.. p$ 

Definimos el Lagraneando de la siguiente forma: 
```ad-important

Definimos el `Lagraneando` del problema como $L: \mathbb{R}^n \times \mathbb{R}^m \times \mathbb{R}^p  \rightarrow \mathbb{R}$ como:
$$
L(x,\lambda, \mu) = f_0(x) + \sum_{i=1}^{m} \lambda f_i(x) + \sum_{j=1}^{p}\mu_jh_j(x)
$$
```


Notar que lo anterior permite convertir "restricciones duras" en "suaves", ya que cuando las mismas "no se cumplne", en realidad lo que hacemos es penalizar a la funcion de costo cuando no se cumplen.

Por otro lado, tenemos la funcion dual. 

```ad-important
La `funcion dual` es la siguiente:

$$
g(\lambda, \mu) = inf_{x \in D} L(x, \lambda, \mu)
$$

Notar que esto es el infimo del `Lagrangenao`
```

## Observaciones importantes
#### Funcion dual es convexa Convexa 
```ad-warning

La funcion $g$ es convexa, independientemente de $f_0$, $f_{1..m}$ y $h_{i..p}$
```
**Demo:**
	Notemos que si fijamos la $x$, entonces la función $f_0(x) + \sum_{i=1}^{m} \lambda f_i(x) + \sum_{j=1}^{p}\mu_jh_j(x)$ lineal con respecto a $\lambda, \mu$. Por lo tanto es tanto convexa como cóncava. Luego el supremo (e infimo) de una función conexa es convexa, por lo tanto el $inf_{x \in D} \sum_{i=1}^{m} \lambda f_i(x) + \sum_{j=1}^{p}\mu_jh_j(x)$ es convexo, siendo $g$ convexa. 

Es importante notar lo siguiente: Si la $f$ es super complicada de trabajar, su funcion dual es "facil", ya que es convexa. 

#### Cada $g(\lambda, \mu)$ es una Cota inferior para la solución del problema primal
Si $\lambda_i \geq 0$, entonces $g(\lambda, \mu) \leq p^*$ (donde $p^*$ es la solución del problema primal). 
Entonces cada solución del problema dual es el realidad una cota inferior para la solución del problema primal. 



## Problema dual
Siguiendo con la idea anterior, el máximo de estas cotas inferiores es la solución buscada. 

```ad-important

El problema dual es el siguiente:

$$max_{\lambda_i \geq 0} \text{ } g(\lambda, \mu)$$
```

Al valor optimo del problema dual se lo denomina $d^*$. 


## Propiedad (Dualidad Debil) 
Siempre ocurre que $d^* \leq p^*$. 
Esto te va a dar la mejor cota inferior para $p^*$ que el problea dual puede dar. 

A la diferencial $p^* - d^*$ se le llama `duality gap`. 

## Propiedad (Dualidad fuerte)
Decimos que tenemos `dualidad fuerte` cuando el duality gap es cero. O sea $d^* = p^*$. En otras palabras, transformamos un problema dificil en uno fácil, y la solución es la misma.

Hay que saber que: 
- No es cierto en general
- Si el primal es convexo, hay dualidad fuerte. 
- Puede ser cierto aun, aunque el primal no sea convexo. 


## Complemento Sleeknoss
Si $x^*$ es un optimo del primal, y ($\lambda^*$,$\mu^*$) del optimo del dual. 
Entonces 
$$\lambda_i f_i(x^*) = 0 \text{  } \forall i =\ 1 .. n$$ Notar que tiene que ocurrir alguno de los dos siguientes casos: $\lambda_i=0$ o $f_i(x^*) = 0$. Si cuando se resuelve el problema, los `multiplicadores de lagrange` ($\lambda_i$) son cero, entonces lo que significa que esa restricción no estaba "jugando" en el problema. En otras palabras, su aplicación no cambia la solución optima. 

## Condiciones de Karrush-Kuhn-Tucker (KKT) 
Se tiene que dar 4 condiciones, que son las siguientes: 
1. Las restricciones del primal se cumplen ($f_i(x) \leq 0$, $h_j(x) = 0$ )
2. Las restricciones del dual se cumplen ($\lambda_i \geq 0$ )
3. Se cumple el "Complemento de Sleeknoss" (Mirar seccion de arriba)
4. $\nabla_\lambda L = 0$ (Gradiente segun $\lambda$ ). Se puede ver que:
	$$\nabla f_0(x) + \sum_{i=1}^m \lambda_i \nabla f_i(x) + \sum_{j=1}^p \mu_j\nabla h_j(x) = 0$$


## Observaciones de KKT
- Si hay Dualidad fuerte $\Rightarrow$ los KKT se cumplen para cada ($x^*, \lambda^*, \mu^*)$ 
- Si ademas el primal es convexo, entonces:
		($x^*$, $\lambda^*$, $\mu^*$) es optimo $\Leftrightarrow$ Cumplen KKT