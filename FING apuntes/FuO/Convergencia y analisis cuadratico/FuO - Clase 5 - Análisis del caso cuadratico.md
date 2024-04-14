
Vamos a trabajar con esta función $f: \mathbb{R}^n \rightarrow \mathbb{R}$ con $f(x) = \frac{1}{2}x^TQx$ con $Q \in S_{++}^n$.

Notemos lo siguiente:
- $\nabla f(x) = Q x$
- $\nabla^2 f(x) = Q$ 
- El mínimo se da trivialmente en x = 0

Observemos que este caso no es "tan de juguete", ya que se trata de un taylor, y por ende sirve para estudiar el comportamiento cerca del optimo.

![[FuO - Clase 5 - Análisis del caso cuadratico 2024-04-14 02.16.55.excalidraw]]

Notemos que para que el método siquiera convenga, el $\alpha$ elegido tiene que cumplir que $max\{ |1-\alpha m|,|1-\alpha M| \} < 1$.

Dibujemos las dos expresiones y la función máximo en función de $\alpha$.

![[FuO - Clase 5 - Análisis del caso cuadratico 2024-04-14 02.43.15.excalidraw]]
Por el siguiente analisis se concluye que el metodo desenso por gradiente solo converge si $\alpha \in (1/M, 2/M)$ 

Ademas el punto optimo es $\alpha_{opt} = \frac{2}{M+m}$ y el valor del máximo es $\frac{M-m}{M+m}$ 

Observemos que el `numero de condicion` es $k = \frac{M}{m}$. Entonces el valor máximo sera $\frac{k-1}{k+1}$.

**Importante**
Notar que nosotros queremos que  $\frac{M-m}{M+m}$ sea lo mas chico posible, para ello **lo ideal seria que la $M$ fuera lo mas cercano posible a $m$**, de forma que $M-m$ se paresca a cero lo mas posible. SI eso ocurre, lo ideal seria que el  `numero de condicion sea lo mas cercano a 1`. 

