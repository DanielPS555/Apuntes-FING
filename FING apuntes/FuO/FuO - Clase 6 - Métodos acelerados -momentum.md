#@ Dudas
-[ ] Cuando buscamos el $\alpha$, ¿deberiamos buscar M y m como vap.propios para encontrar el $\alpha$ y/o $\beta$. 
-[ ] Es mucho peor saber $\alpha$ y/o $\beta$ (o sea el numero de condicion) que poder encontrar $m$ o $M$?

## Def (L-Lipsehiptz)

$g$ es `Lipsehitz` sii $|| g(x) - g(z) || \leq L ||x-z||$  $\forall x,y$
Obs: La L del nombre sale del parámetro de compresión/expansion.

### Prop
Si $f$ tiene $\nabla f$ de `M-lipsehiptz` entonces $f(z) \leq f(x) + \langle \nabla f(x) , z-x \rangle + \frac{M}{2} + ||z-x||^2$ 

Notar que con esa propiedad, y considerando la desigualdad de que sea convexa estricta, podemos entonces dos funciones que encieran a $f$


![[FuO - Clase 6 - Métodos acelerados -momentum 2024-04-22 00.42.44.excalidraw]]

### Observacion (`Importante`)
`m` y `M` son los valores propios mas chico y mas grande de $\nabla^2 f$.


### Recordar:
Sea $cond$ el numero de condiicon de una matriz, donde $cond = \frac{M}{m}$ , vimos que si tenemos paso fijo, en el caso cuadratico podemos conseguir una velocidad de convergencia a lo mejor de 

$$||x_k , x^*|| \leq (1- \frac{2}{cond + 1}) ^ k ||x_0-x^*||$$

## Prop (`Importante`)
Si $f$ es `estrictamente convexa` y $\nabla f$ `Lipsihtz` entonces si elegimos $\alpha = \frac{2}{M+m}$ se cumple que la `taza de convergencia`: $||x_k - x^*|| \leq (1- \frac{2}{cond + 1}) ^ k ||x_0-x^*||$

### Observación (`Importante`)
Si utilizamos otra técnica para elegir el paso (Ej: Armijo, Linea Serach) `no cambia la taza de convergencia`. Debe cambiar el metodo, por ejemplo usar newton.

### Conclucion y pregunta (`Importante`)
Sabemos que descenso por gradiente nos permite tener métodos de orden lineal, con information de segundo orden (derivada segunda) podemos obtener convergencia cuadrática. ¿Podemos hacer algo mejor sin segundo orden?



## Método Hezwg-beth

Podemos intentar eliminar el zig-zag añadiendo algo similar al "rosamiento" en física (ideas locas de Fiori...). Pero esencial se ve asi:

- $x_{k+1} = x_k + \alpha p_k$
- $p_k = - \nabla f(x_k) + \beta p_{k-1}$  

O sea, por medio de un $\beta$ se utiliza en mas o menos medida la información de la anterior dirrecion. O sea el método tiene "memoria" y utiliza para elegir la nueva dirrecion la información de la anterior dirrecion.

El método `hezwg-beth` es cuando $\alpha, \beta$ es constante.

Si $f$ es cuadrática es lo conoce como método `Chebyshev`. 


#### ¿Se mejora la convergencia con este método?


En el video 6 hace un poco de análisis, solo añado aquí los resultados. 

Se consigue un `mejora significativa` en la taza de convergencia de $1 - \frac{2}{\sqrt{k} + 1}$ cuando:
- $\alpha = \frac{4}{M} \frac{1}{(1 + 1/\sqrt{cond})^2}$ 
- $\beta = (1 - \frac{2}{\sqrt{cond} + 1})^2$  


Notar que tiene el problema que precisamos saber el `numero de condicion`.


## Método de Nesterow

Es similar al anterior, pero es mas explicito  en cuanto a los parámetros.

Hay dos formas de escribirlo, pero son lo mismo:

Primera forma:
- $x_{k+1} = y_{k} - \alpha_{k} \nabla f(y_k)$ 
- $y_k = x_k + \frac{k-1}{k+2}(x_{k}-x_{k-1})$ 
Otra forma:
- $x_{k+1} = x_k + \alpha_{k} p_k$
- $p_k =  -\nabla f(x_k + \beta_k (x_k - x_{k-1})) + \beta_k p_{k-1}$ 

Donde se eligue a $\alpha = \frac{1}{M}$ y se pueden elegir entre varios $\beta$, una opción es por ejemplo $\beta = \frac{k-1}{k+2}$ 

Tenemos la misma tasa de convergencia que antes.

## Cota inferior de tasa de convergencia
Nesterow probo que la mejor tasa de convergencia que se puede obtener con un método lineal es $1 - \frac{2}{\sqrt{k} + 1}$, es que lo que obtenemos con el método anterior. O sea que no vamos a poder mejorar nada mas con métodos de orden lineal.