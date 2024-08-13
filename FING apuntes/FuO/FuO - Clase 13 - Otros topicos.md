Estos topicos son `Relativamente modernos`. 

## Cuando $f$ no es differenciable
- Ya vimos el concepto de sub-gradiente 


Los métodos también se generaliza:
$$x_{k+1} = x_k - \alpha_k d_k$$ con $d \in \partial f(x_k)$. 

- No es siempre cierto que un $d \in \partial f(x_k)$ sea una dirrecion de descenso 
- Lo que perdemos es velocidad!

## Proximal Methods

```ad-info
Dado $f:\mathbb{R}^n \rightarrow \mathbb{R}$ convexa, definimos el operador proximal $prox_{\lambda,f}: \mathbb{R}^n \rightarrow \mathbb{R}^n$ como:
$$prox_{\lambda, f}(z) = argmin_{x} (f(x) + \frac{1}{2\lambda} || x-z ||_2^2)$$

```

No busca donde minimiza $f$, sino donde se minimiza sin alejarse mucho de $z$ 


Obs: Si $f$ es la funcion indicatriz, (0 dentro del conjunto, infinito fuera del conjunto, lo que hace es minimizar un elemento en el conjunto).

```ad-note
$x^*$ es solución de $min_x f(x) \Leftrightarrow x^* = prox_{\lambda, f}(x^*)$  
```


## ADMM (Alternating Directions Method of Multipliers)

Consideremos el problema:

min f(x) + g(x) 
St : Ax + Bz  = c

Contruimos el Lagraneando aumentado

$L_\delta (x,z,\mu) = f(x) + g(z) + \mu^T(Ax+Bz-c) + \frac{\delta}{2} || Ax+Bz - c||_2^2$ 

Realizamos la siguiente interaciones:

$$x_{k+1} = argmin_x L_\delta(x, z_k, \mu_z)$$
$$z_{k+1} = argmin_z L_\delta(x_{k+1}, z, \mu_z)$$
$$\mu_{k+1} = \mu_k + \delta(A x_{k+1} + Bz_{k+1} - c)$$
Obs: Esto se utiliza cuando f y g son faciles, pero la suma no lo es. 


Ejemplo:
Tenemos que optimizar: 
	min f(x) + g(x) 

Se puede tranformar: 
	min f(x) + g(z)
		St: x = z

Esto se uso mucho en metodos como LASSO ($min ||Ax-b||^2 + ||x||$ )


## Stocastic Degres desend 

Tenemos una cantidad absurda de instancias y de parámetros a optimizar:
Es alta mente NO convexa. 

$min_x \sum_{i=1}^N f_i(x)$. Entonces $\nabla f(x) = \sum_{i=1}^N \nabla f_i(x_i)$ 

Como no se puede computar para una cantidad tan grande de parámetros, se eligen $k$ instancias por epoca. 

$$\overline{\nabla(f(x))} = \sum_{i=1}^k \nabla f_i(x)$$
Resulta que $E(\overline{\nabla(f(x))}) = \nabla f(x)$ 

El paso sera: $x_{k+1} = x_k - \alpha_k \overline{\nabla(f(x))}$ 

Esto se utiliza para redes neuronales cuando son millones de parámetros.

Dos preguntas:
1. ¿Porque esto deberia converger a algo? 
		Si: $\alpha$ es tal que $\sum \alpha_k = \infty$ y $\sum \alpha_k <\inf$ 

2. ¿Porque el optimo debería ser bueno?
	No explico!!!



## Convinaciones de trucos

Se pueden combinar las siguientes tecnicas y se obtienen  buenos resultados.

1. Desenso por gradiente estocastico + SubGradientes
2. Desenso por gradiente proyecto + Newton
3. Proximal Method + descenso por gradiente
4. Desenso por gradiente proyectado + Nestrow
5. Desenso por gradiente estocastico + Nesterow

