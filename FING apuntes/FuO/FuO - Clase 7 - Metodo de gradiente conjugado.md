
Método de gradiente Conjugado (mas o menos del 1952 Hestenes y Stiefe)


Sea $A \in \mathbb{R}^{n \times n}$ simetrica y definida positiva ($A \in S_n^{++}$).

Se puede pensar de dos formas que en este contexto con equivalente:
- Para resolver $Ax = b$ 
- Para buscar el mínimo de $min_{x} \frac{1}{2} x^T A x - b^T x$ 

O sea una `x` que resuelva uno de estos problemas resuelve el otro tambien.

Notar que los problemas equivalentes, ya que:

![[FuO - Clase 7 - Metodo de gradiente conjugado 2024-05-05 14.50.55.excalidraw]]



## Observaciones importantes
- Este método es considerado el `estado del arte` para este tipo de problemas.
- Muy util cuando $n$ es grande ($n >> 1$).
- Es particularmente buena cuando $A$ es `esparsa` (dispersa)
- No es necesario tener $A$ en memoria, sino solo necesitamos saber $A.v$ 
- Tiene `garamtia` que la convergencia se alcanza en `n iteraciones`
- Por lo general no es necesario correr hasta el final ($n$ iteraciones), se pueden en pocas iteracion muy buenas aproximaciones.
- funciona `mucho mejor` cuando los valores  propios están `clusters`. Esto significa que los valores propios están agrupados en uno o varios clusters (o grupos) y no están dispersos de forma uniforme entre el valor propio mas grande y el mas chico.  



## El metodo

Llamaremos `residuo` $r = b - Ax$ (notaf que es igual a $-\nabla f(x)$) 

Vamos a generar $x_k$ (con sus respectivos $r_k$)

Vamos a ver cada enfoque


#### Enfoque 1º
Se basa en los `subespacios de Krylov` los cuales se definen con:
$$

K_k = span\{b, Ab, A^2b, ..., A^{k-1}b\}
$$
> "span" es espacio generado

Luego la secuencia $x_k$ esta definida como:
$$
x_k = \text{argmin }f(x) \text{ con } x \in K_k$$

Para ciertos $\alpha_k, \beta_k$ se cumple que 
$$

x_{k+1} = x_k + \alpha_k r_k + \beta_k (x_k - x_{k-1})

$$

Notar que esto tiene mucha relación con los métodos con `momentum` ya que como $r = -\nabla f(x)$ tenemos un descenso por gradiente, pero utilizando la información de dos pasos anteriores.Vamos a analisarlo mejor en el segundo  enfoque.


#### Enfoque 2º

Pensemos en un método $x_{k+1} = x_k + \alpha_k . d_k$ 

Vamos a movernos por direcciones $d_k$, relacionadas con $- \nabla f(x)$ , pero no exactamente.

El dos direcciones son `conjugadas` si: 
$$
d_{k-1}^T A d_k = 0
$$
Esto es $\langle d_{k-1}, d_k \rangle_A$ Lo que es el producto interno inducido por $A$. 
Esto lo que intenta es adaptar el concepto de ser `perpendicular` al problema configurado por $A$. 
Es lo mismo que decir `que las dirreciones seran ortogonales por A`. 


Por lo tanto el método sera el siguiente:

- Primero elegimos la dirrecíon $d_k$, de la siguiente forma:
		$d_k = r_k + \beta_k . d_{k-1}$ pero nos queremos asegurar que $d_{k}$ y $d_{k-1}$ sean conjugadas según A, eso es $d_{k-1}^T A d_k = 0$. 
		Para ello elegimos $$\beta_k = -\frac{r_k^TAd_{k-1}}{d_{k-1}^TAd_{k-1}}$$ 
		
- Luego podemos calcular cual es el mejor $\alpha_k$ para la dirrecíon elegida $$\alpha_k = - \frac{r_k^Td_k}{d_k^TAd_k}$$
- Con ambos datos podemos calcular $x_{k}$ 

#### Pseudo codding 
(foto clase)

![[Pasted image 20240505165914.png]]

`Importante`
Notar que podemos escribir el paso 3º de la siguiente forma: 

$r_{k+1} = b - Ax_{k+1}$ 
	 $= b - A(x_k - \alpha_k d_k)$
	 $= b - A.x_k - \alpha_k A d_k$ 
     $= r_k - \alpha_k A d_k$  

### Solo precisamos $Ad_k$ (`Importante`)
- Notar que con la re-escritrua del paso 3º, la `parte mas pesada del proceso`, que es multiplicar A por un vector, resulta que es siempre el mismo vector. En otras palabras siempre que aparece $A$ en las operaciones es de la forma $Ad_k$.
		En otras palabras, `solo presidamos saber` el $Ad_k$ `para poder realizar el proceso`.


### Criterio de parada
Tenemos `asegurado` que en $n$ iteraciones $r_n = 0$, eso sirve para la solución exacta. De todas formas podemos buscar una aproximada con  $r_k = tolerancia$


### ¿Solo para problemas cuadráticos?
Hay formas de aplicarlo a problemas que no son cuadráticos, pero ahí se vuelve mas complejo.


### Problemas auxiliares
Se puede aplicar en la solucion de problemas auxiliares, como por ejemplo encontrar la derivada segunda (heziana) en la resolucion del metodo de Newton