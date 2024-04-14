
Es cuando estamos trabajando en todo el dominio de $\mathbb{R}^n$
O sea 

![[FUO - clase 4 - Optimization sin Restriccion 2024-04-10 01.12.31.excalidraw]]


## Recordemos: Condicíon necesaria de optimalidad

$f:\mathbb{R}^n \rightarrow \mathbb{R}$  diferenciable, $x^*$ mínimo local de $f$ entonces $\nabla f(x^*)= 0$ 
Si ademas $f \in C^2$, entonces $\nabla² f(x^*)$  (hezziana) es semi-definida positiva.

Demo (solamente primera parte): 

![[FUO - clase 4 - Optimization sin Restriccion 2024-04-10 01.17.06.excalidraw]]



## Proposición (`Super importante`)

Si $f$ es diferenciable y convexa, entonces $\nabla f(x^*) = 0$ es `condicion necesaria y suficiente` para que $x^*$  sea mínimo global

Demo:

Ya probamos que si es minimo local (en particular global) entonces el gradiente es cero. Nos falta el reciproco.

![[FUO - clase 4 - Optimization sin Restriccion 2024-04-10 01.35.39.excalidraw]]

