

### Definicion



### Propiedad (Derivada mayor significa mayor crecimiento)

$$
\frac{\partial f}{\partial v} (p) > \frac{\partial f}{\partial w} (p) 
\Rightarrow \forall t: 0<t<\epsilon \text{, se cumple que } f(p + tv) > f(p + tw)

$$

### Corolario
Notar que con el anterior teorema podemos afirmar que si crese mas en una dirrecion, en la dirreción opuesta es donde mas decrese.  
- $t\in(0,\epsilon), f(p + tv) - f(p+tw) > 0$
- $t\in(-\epsilon,0), f(p + tv) - f(p+tw) < 0$

### Corolario
Si $\frac{\partial f}{\partial v}(p) > 0$ $\Rightarrow$ $v$ es una direction de crecimiento

### Corolario `Importante`
> El gradiente es la direction de mayor crecimiento


### Condición necesaria de optimalidad
Un `minimo` / `maximo` cumple `necesariamente` que $\nabla f(x) = 0$ 


## Matriz Jacoviana
Si $f: \Re^{n} \rightarrow \Re^{m}$ y $p \in \Re^{n}$

Entonces: 
- $df_p = J_f(p).x$ 

Donde si $f = (f_1, f_2, f_3, ... , f_n)$

$$
\Rightarrow J_f(p) = \begin{pmatrix}
--- & \nabla f_1(p)^t & --- \\
--- & \nabla f_2(p)^t & --- \\
--- & \nabla f_3(p)^t & --- \\
--- & ... & --- \\
--- & \nabla f_n(p)^t & ---
\end{pmatrix}
$$

### Propiedad
- $J_{f+g}(p) = J_f(p) + J_g(p)$ donde $f, g : \Re^n \Rightarrow \Re^m$ (Diferencable en p)
- $J_{f.g}(p) = J_f(p).g(p) + J_g(p).f(p)$
- $J_{f \circ g}(p)= J_f(g(p)).J_g(p)$






$\nabla L(x,\lambda) = \nabla (q(x) - \lambda g(x))$
		 $= \nabla q(x) - \nabla(\lambda(||x||^2 - 1))$
		 $= \nabla q(x) - \nabla \lambda ||x||^2 + \nabla \lambda$
		$$
		= \begin{pmatrix}
\frac{\partial q(x)}{\partial x}\\
\frac{\partial q(x)}{\partial \lambda} 
	\end{pmatrix} 
	- 
	\begin{pmatrix}
\frac{\partial \lambda ||x||^2}{\partial x}\\
\frac{\partial \lambda ||x||^2}{\partial \lambda} 
	\end{pmatrix}
	+ 
	\begin{pmatrix}
\frac{\partial \lambda}{\partial x}\\
\frac{\partial \lambda}{\partial \lambda} 
	\end{pmatrix}
	
	$$
	$$
		= \begin{pmatrix}
\frac{\partial q(x)}{\partial x}\\
0 
	\end{pmatrix} 
	- 
	\begin{pmatrix}
\frac{\partial \lambda ||x||^2}{\partial x}\\
|x||^2 
	\end{pmatrix}
	+ 
	\begin{pmatrix}
0\\
1 
	\end{pmatrix}
	
	$$

			



