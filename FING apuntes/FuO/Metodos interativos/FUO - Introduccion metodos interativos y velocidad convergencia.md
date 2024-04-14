Construimos una succession $\{x_k\}$ en $\mathbb{R}^n$ tal que $x_t \rightarrow x^*$. 

Hay muchas cosas que no interesan ademas que la sucesión converga a la solución, por ejemplo:
- Con que velocidad converge

Para ello se define una `funcion de error`, $e:\mathbb{R}^n \rightarrow \mathbb{R}^+$ que cumple que $e(x^*) = 0$

Algunos ejemplos de estas son: 
- $e(x) = ||x-x^*||$
- $e(x) = |f(x) - f(x^*)|$

Observar que: $e(x_k) \rightarrow 0$

¿Que tan rápido tiene a cero?

#### Convergencia lineal

Un método tiene convergencia lineal si 

![[Drawing 2024-04-05 21.02.51.excalidraw]]
Notar que es lineal con respecto al cociente, pero es exponential con respecto al error, ya que:

$e(x_n) = e(x_0).\beta^n$

#### Convergencia supra-lineal:
![[Fuo - Clase 2 2024-04-05 21.08.39.excalidraw]]

#### Convergencia cuadrática:
Cuando obtenemos un metodo con esta velocidad, se lo considera MUY BUENO.

![[Fuo - Clase 2 2024-04-05 21.10.01.excalidraw]]


Observacion: Cuando es Convergencia Cuadratica $\Rightarrow$ convergencia supralineal $\Rightarrow$ convergencia lineal.
