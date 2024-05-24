
Vamos a trabajar con:

$$
min_{x \in X} f(x) \text{ con } f \text{ diferenciable y } X \text{ convexo}$$ 
```ad-info
A un punto $x$  que cumple las restricciones lo llamamos `factible`
```

## Condiciones de optimalidad

a. Si $x^*$ es un mínimo local, entonces $$\forall z \in X, \langle \nabla f(x^*), z-x^* \rangle \geq 0$$
b. Si ademas $f$ convexa, entonces **(a)** es suficiente.

Algunas observaciones:
- Como $X$ es convexo, entonces $z - x^*$ son `dirreciones factibles` desde $x^*$.
- Pedir que $\forall z \in X, \langle \nabla f(x^*), z-x^* \rangle \geq 0$, es pedir que el angulo entre el gradiente y cualquier dirrecion factible, tenga un angulo entre (-90º, 90º).
	![[FuO - Clase 9 - Optimization sin restricciones - condiciones de optimalidad 2024-05-19 23.08.24.excalidraw]]
	Notar que para que lo anterior sea en efecto una condición necesaria, es importante que $X$ sea convexa. 

## Ejemplo (Proyecciones)

![[FuO - Clase 9 - Optimization sin restricciones - condiciones de optimalidad 2024-05-19 23.47.43.excalidraw]]

```ad-attention

Si $X$ es un espacio vectorial, el conjunto es una "recta", y por lo tanto se cumple que:

$$\forall x \in X, \langle z - P_x(z), z-x \rangle = 0$$

O sea, que $z-P_x(z) \in X^{\perp}$
```

Si continuamos usando lo anteriormente deducido en el ejemplo se puede concluir que:

```ad-success

Sea x,y \in \mathbb{R}^n y sus proyecciones a X, P_X(x), P_X(y).

Entonces: $$|| P_X(x) - P_X(y) || \leq ||x-y||$$

Esto es, `La proyeccion es NO expansiva`
```


## Forma alternativa de condición de optimalidad

Utilizando el ejemplo anterior, mas alguna cuenta se puede escribir la condición de optimalidad de esta otra forma: 

```ad-important
Escritura alternativa de la condicion de optimalidad

$$x^* = P_X(x^* - \nabla \alpha f(x^*)), \forall \alpha > 0 $$ 

Se la conoce como `Condicion de estacionalidad`
```

Notar que lo anterior lo que nos dice es que si estamos parados en el optimo, nos movemos en la dirrecion de mayor decrecimiento ($\nabla f(x^*)$) y luego proyectamos, entonces NO nos movimos.


## Análisis pero sin que sea diferenciable

#### Definición (subgradiente)
Sea $f$ convexa, decimos que $d \in \mathbb{R}^n$ es un `subgradiente` de $f$ en $x$ sii:
$$
f(z) \geq f(x) + \langle d, z-x \rangle, \forall z \in \mathbb{R}^n
$$

#### Definición
Al conjunto de gradientes en $x$ se lo llama `subdiferencial` $\partial f(x)$ 
Ejemplo: Si $f(x) = |x|$ entonces $\partial f(0) = [-1,1]$ 


#### Proposición
$f : X \rightarrow \mathbb{R}$  convexa, $X$ convexa, entonces $x^*$ minimiza $f$ en $X$ sii:
$\exists d \in \partial f(x^*)$ tal que $\langle d, z-x^* \rangle \geq 0$ $\forall z \in X$ 
Observaciones: 
1. Si $f$ es differentiable, recuperamos que $\langle \nabla f(x^*), z-x^* \rangle \geq 0$ $\forall z \in X$ 
2. Si $x^*$ es un punto interior a $X$, la condición es que $0 \in \partial f(x^*)$.
		Notar que significa que la recta con pendiente cero que pasa por $x^*$ esta por debajo de toda la gráfica, o sea es un mínimo local (absoluto por ser convexa)


## Intepretacion geometrica

#### Definicion (Cono normal)
Llamaremos `cono normal` de $X$ por $x$ al conjunto $$N_X(x) = \{g\mathbb{R}^n: \langle g, z-x \rangle \leq 0, \forall z \in X\}$$
Notar que eso en el caso que sea diferenciable, es solamente el $-\nabla f(x)$. 

```ad-important
Si definimos a $C = \{z\in \mathbb{R}^n: f(z) \leq f(x_0) \}$ 
Es fácil notar que si $d \in \partial f(x_0) \Rightarrow d \in N_C(x_0)$ 


```
![[FuO - Clase 9 - Optimization sin restricciones - condiciones de optimalidad 2024-05-20 01.39.29.excalidraw]]


Eso generaliza la idea que el gradiente es perpendicular a las cubras de nivel.

```ad-important
Condicion de optimalidad


$$\exists d \in \partial f(x^*) \text{ tal que } \langle d, z - x^* \rangle \geq 0, \forall z \in X$$
En otras palabras

$$ \exists g \in \partial f(x^*) \text{ tal que } -g \in N_X(x^*)$$

```

Ejemplo cuando $f$ differenciable pero $X$ no es suave

![[FuO - Clase 9 - Optimization sin restricciones - condiciones de optimalidad 2024-05-20 01.55.49.excalidraw]]


Ejemplo cuando $f$ no es diferenciable pero X si es suave

![[FuO - Clase 9 - Optimization sin restricciones - condiciones de optimalidad 2024-05-20 02.01.40.excalidraw]]