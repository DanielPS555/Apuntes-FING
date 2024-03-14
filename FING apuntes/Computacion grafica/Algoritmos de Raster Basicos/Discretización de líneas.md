Los algoritmos que vamos a utilizar funcionan con $0 \leq m \leq 1$ (45º), aqui iteramos las $x$ para encontrar las $y$. 
Si estamos para $m \geq 1$ utilizamos la misma formula, pero variando $y$ para encontrar $x$.  


#### Primer algoritmo
$y_i = mx_i + b$
Y se elige el pixel pintar: $(x_i, round(y_i))$ 

Notemos que hay dos problemas:
1. Utiliza `punto flotante`, el cual es mas lento que operación con enteros
2. No aprovechamos los `calculos anteriores` en los nuevos pixeles. Por lo tanto  realizamos mas cuentas.


#### Segundo algoritmo
Notemos que si $y_i = mx_i + b$ entonces:
$y_{i+1} = m.x_{i+1} + B = m(x_i + \Delta x) + b = y_i + m.\Delta x$

Ademas si $\Delta x = 1$, entonces: $y_{i+1} = y_{i} + m$ 

Notemos que en ese algoritmo se ha disminuido el numero de cuentas. ``Dejaste de hacer un producto``.

#### Tercer algoritmo: Algoritmo de lineal de punto medio
Aquí se va a usar ``Arismetica entera``, no punto flotante y se lo puede mejorar para utilizar calculos acumulativos. 

Asumamos que estamos en un punto intermedio del algoritmo. Donde en el anterior paso se ha seleccionado el pixel con ordenadas $(x_p, y_p)$. Tenemos dos opciones para el paso actual dadas las precondiciones actuales: 
- Elegimos el pixel siguiente sin aumentar el tamaño - Llamado `E`: $(x_p + 1. y_p)$
- Elegimos el pixel una altura mayor- Llamado `NE`: $(x_p + 1, y_p + 1)$

![[Pasted image 20240310235644.png]]

Notemos que si trazamos la función de la recta de la siguiente forma: $mx + b - y$ se cumple que si:
- El `punto esta en la recta`, entonces el valor será ``cero``.
- El ``punto esta por debajo`` de la recta será ``positivo``.
- El ``punto esta por arriba`` de la recta será ``negativo``.
Entonces lo que hacemos es ``evaluar en la función el punto medio`` entre los dos posibles pixeles a prende. Si la recta esta por ensima del punto medio (positivo) entonces elegimos `NE`, sino elegimos el `E`. 


La formula $f$ se puede expresar de la siguiente forma, donde todos son enteros. $y = \frac{dy}{dx} x + b$ de la siguiente forma: 

$F(x,y) = ax + by + c$ donde:
- $a = dy$
- $b = -dx$
- $c = b.dx$

Notar que quedaría de la siguiente forma: $F(x,y) = dy.x - dx.y + b.dx$ 

Notar que el mecanismo seria computar $d = F(x_p + 1, y_p + \frac{1}{2})$. Y elegir si será NE si $d > 0$ o en caso contrario E.

Intentemos ahora utilizar el calculo del $d$ anterior para poder calcular el siguiente. 

Si $d_{p+1} = a(x_p + 1) + b(y_p + \frac{1}{2}) + c$. Veamos si podemos con esto calcular $d_{p+2}$.

Hay dos casos: Si el pixel elegido en el paso $p+1$ es el pixel E o el pixel NE.

**Caso 1 (Se eligió en el paso p+1 pixel E):** 
	$d_{p+2}$ $=$ $a(x_p + 2) + b(y_p + \frac{1}{2}) + c$
		 $= (a(x_p + 1) + b(y_p + \frac{1}{2}) + c) + a$
		 $= d_{p+1} + a$
		  $= d_{p+1} + d_y$
		 $= d_{p+1} + \Delta_E$
		
**Caso 2 (Se eligió en el paso p+1 NE)**: 
$d_{p+2}$ $=$ $a(x_p + 2) + b(y_p + \frac{3}{2}) + c$
		 $= (a(x_p + 1) + b(y_p + \frac{1}{2}) + c) + a + b$
		 $= d_{p+1} + a + b$
		 $= d_{p+1} + dy - dx$
		 $= d_{p+1} + \Delta_{NE}$
		
Con esto se nota que si se calcula $\Delta_E$ y $\Delta_{NE}$ en un inicio, el siguiente paso es simplemente una suma (con su comparación).


##### Observación en el paso inicial

Para la recursión precisamos el primer $d_1$, para ello si queremos dibujar una recta desde $(x_0, y_0)$, se cumple que: $d_1 = F(x_0 + 1, y_0 + \frac{1}{2}) = F(x_0, y_0) + a + \frac{b}{2}$. 

**Observación**: si $b = -dx$ es ``impar`` tenemos un problema ya que no se podrá operar en entero. Entonces se propone `multiplicar F por 2`. 
Esto ``no modifica el sentido de cuando d es mayor igual o menor a cero``. 

Entonces se utiliza $2F(x,y) = 2ax + 2by + 2c = 2d_yx - 2d_xy + 2d_x.b$ 
