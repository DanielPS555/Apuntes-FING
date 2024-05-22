Sea $f: X \subset \mathbb{R}^n \rightarrow \mathbb{R}$ convexa, diferenciable
$X = X_1 \times X_2 \times ... X_m$ con $X_i \subset \mathbb{R}^n_i$ donde $\sum_i^m n_i = n$ 
y $x \in X$ escrito de la siguiente forma $x = (x_1, x_2, ... x_m)$ ( o sea $x_i \in X_i$)


Vamos a generar una secuencia $x^1, .... x^k$ como siempre (Usamos los supra-indices para no confundir con lo del parafo anterior)

Actualizaremos las corrdenadas de esta forma:

```ad-important

$x_i^{k+1} = argmin_{x \in \mathbb{R}^n_i} f(x_{1}^{k+1}, x_{2}^{k+1},  ... , x_{i-1}^{k+1}, x, x_{i+1}^{k}, ... x_{m}^{k})$

```


Notar que para pasar de un paso a otro, hay que ir actualizando cada coordenada (Cuidado que son bloques) de a una, hasta recorrer $1..m$. 
O sea, minimizamos en cada paso de a partes. 

Notar que los bloques se arman dependiendo de la funcion. 


Si $x$ en cada coordenada es un mínimo local, ¿$x$ es un minimo local? 
**Hay ejemplos que muestra que esto no es asi**

![[FuO - Clase 8 - Coordinate descent 2024-05-19 20.20.00.excalidraw]]

Este ejemplo la funcion no es $C^1$


### Preposicion (`Importante`) 

> Demo dentro de Bertsekas

Sea $f : \mathbb{R^n} \rightarrow \mathbb{R}$ es convexa y $C^1$, entonces $X = x_1, ... x_n$ un $X_i$ convexos, si $f(x_1, x_2, ..., x_{i-1}, z, x_{i+1}, ... , x_n)$ mirada como función de $z$ tiene un único mínimo en $X_i$, entonces la sucesión generada por el método cumple que todo punto limite minimiza f.

```ad-note
Hay aplicaciones donde este metodo es el  estado del arte
```



