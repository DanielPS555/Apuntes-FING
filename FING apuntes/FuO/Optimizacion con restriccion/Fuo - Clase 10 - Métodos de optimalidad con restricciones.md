
Vamos a pedir que:
- $X$ sea convexo y cerrado
- $f$ differenciable


Vamos a buscar metodos de la forma 
$$x_{k+1} = x_k + \alpha_k d_k$$
Tal que $d_k$ tiene que ser **factible** y de desenso.

Recordemos que:
	$d_k$ es **factible** si $d_k = x - x_k$ para algún $x \in X$.


## Método de Frank-Wolfe
Tambien llamado `Gradiente condicional`

hay que elegir $d_k = \overline{x_k} - x_k$ y tiene que ser de decenso, o sea: $\langle \nabla f(x_k), \overline{x_k} - x_k \rangle < 0$    

Observación: 
	Notemos que si no existe un $x \in X$ que cumpla lo anterior, entonces $\forall x \in X$ se cumple que $\langle \nabla f(x_k), \overline{x_k} - x_k \rangle \geq 0$ que es la condicion de optimad, por lo que el proceso termina, ya que se llego a un punto estacionario.

Entonces elegimos un $\overline{x_k}$ que `minimiza` $\langle \nabla f(x_k), \overline{x_k} - x_k \rangle$ . 

```ad-note
O sea que en cada paso buscamos:

$$
\overline{x_{k+1}} = argmin_{x \in X} \langle \nabla f(x_k), \overline{x_k} - x_k \rangle
$$

```

Observar que lo anterior es un problema de optimizacion en si mismo, pero al mismo tiempo es en una sola variable ($x$), por lo que debería ser mas simple. 

El paso $\alpha_k$  lo podemos elegir como Gradiente conjugado (Por ejemplo elegir Armijo).


## Método del gradiente proyectado

El método se realiza de la siguiente forma: 
```ad-note
$$x_{k+1} = x_k + \alpha_k d_k = x_k + \alpha_k (\overline{x_k} - x_k)$$

donde $$\overline{x_k} = P_X(x_k - s_k \nabla f(x_k)) $$ con $\alpha_k \in (0,1]$ 
```

Notemos que si elegimos $\alpha_k = 1$
entonces: $x_{k+1} = P_X(x_k - s_k \nabla f(z_k))$

![[Pasted image 20240524022855.png]]

```ad-info
El método termina cuando ya no avanza mas, eso significa que $x_k = P_X(x_k - s_k \nabla f(z_k))$ 
```

Algunos comentarios importantes: 


```ad-hint
Se puede acelerar a nivel de `Nesterow` de la siguiente forma

$y_k = x_k + \beta_k (x_k - x_{k-1})$ con $\beta = \frac{k-1}{k+2}$ 
$x_{k+1} = P_X(y_k - s_k \nabla f(y_k))$
```

