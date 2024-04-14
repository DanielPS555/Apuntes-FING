
Sea $f : R \rightarrow R$ busquemos la solución al siguiente problema.

Comencemos con algo acotado en $a,b \in R$

![[FUO - Clase 2 - Algunos métodos básicos de optimización en R 2024-04-05 21.32.31.excalidraw]]



### Grid search
Si es barato evaluar la imagen y no se requiere una solución con mucha presicion, entonces se puede aplicar el siguiente método. 

![[FUO - Clase 2 - Algunos métodos básicos de optimización en R 2024-04-05 21.34.47.excalidraw]]

Generamos una recta con $n$ divisiones (o una grilla en dimensiones superiores) y calculamos la imagen en cada division. Tomamos el mínimo de ellas. 


### Biparticion

Es la aplicacion del teorema de Bolazno. Reduciendo a la mitad el intervalo en cada paso.

`Esto sirve para raizes no para minimos`


### Golden section

Vamos a trabajar con $f$ `unimodal`.

Inicialmente vamos a tener 3 puntos, $\{x_1,x_2,x_3\}$, vamos a generar $x_4$ de forma tal de poder descartar algunos de los segmentos. 

Observar que hay dos posibles casos:

f(x_4) > f(x_2)

![[FUO - Clase 2 - Algunos métodos básicos de optimización en R 2024-04-05 22.53.54.excalidraw]]


f(x_4) < f(x_2)

![[FUO - Clase 2 - Algunos métodos básicos de optimización en R 2024-04-05 22.56.32.excalidraw]]


Nos gustaría:
1. Que los intervalos posibles a eliminar sean iguales en tamaño (así no hay preferencia)
2. En cada paso, el largo del intervalo se reduzca un factor contante (como en el método de bi-partición)

Para cumplir lo primero se puede hacer lo siguiente:
	Notemos que en cada comienzo de iteracion, los puntos $\{x_1, x_2, x_3\}$ están dados. Por observando el siguiente gráfico, solo puedo determinar $c$. Ya que $a$ y $b$ ya están determinados

	![[FUO - Clase 2 - Algunos métodos básicos de optimización en R 2024-04-05 23.01.58.excalidraw]]
Para cumplrir lo segundo, tenemos que buscar que $\frac{\text{longitud segmento iteracion i}}{\text{longitud segmento iteracion i+1}}$ sea una constante. En otras palabras:

	![[FUO - Clase 2 - Algunos métodos básicos de optimización en R 2024-04-05 23.23.29.excalidraw]]


> Estos metodos son apropiados para cualquier funcion que evaluar la imagen  no es costo, pero su `derivada` no existe o es costosa de calcular.  


## Desenso por gradiente

La idea es utilizar la siguiente iteracion:

$x_{n-1} = x_n - \nabla f (x_n) . \alpha$ 

En otras palabras vamos en la dirrecion contraria al gradiente. 
Hay que tener cuidado con la elección del $\alpha$. En Aprendizaje automático se dio varias tecnias de como se podría tratar ese valor.

### Método de Newton

Ahora asumamos que la función $f \in C^2$ , por lo tanto calcularemos su polinomio de taylor de segundo grado. 
$$
P_2(x) = f(x_n) + f'(x_n)(x-x_n) + \frac{f''(x_n)}{2} (x-x_n)^2
$$
![[FUO - Clase 2 - Algunos métodos básicos de optimización en R 2024-04-05 23.56.23.excalidraw]]

Donde $x_{n+1}$ sera el minimo del poliomio de taylor antes mencionado.

En otras palabras tenemos que buscar $x$ para que la siguiente exprecion sea cero. 

$$

P'_2(x) = f'(x_n) + f''(x_n)(x-x_n) = 0

$$

La exprecion de $x$ queda como:

$$

x = x_n - \frac{f'(x_n)}{f''(x_n)}

$$
> Observar que esto es lo mismo que el método de `Newton Barpson` pero aplicado en la derivada. Recordemos que el método de Newton-Barpson es el siguiente:
> $$
 x_{n+1} = x_{n} - \frac{g(x_n)}{g'(x_n)}
 $$


Observaciones:
- No siempre funciona, es mas, no se sabe cuando funciona. Por lo general si uno esta `suficientemente cerca del minimo`. ahi si converge, sino el comportamiento es extraño.
- Cuando converge, es muy rápido, es un su velocidad de convergencia es `cuadratico`. 
- Notemos que es muy similar al método de descenso por gradiente, donde $\alpha = \frac{1}{f''(x_n)}$ 
- Este método se puede generalizar a $\mathbb{R}^n$


**Proposicion** (Velocidad de convenregencia para NR = Newton Raphon)
> Es analogo con la demo de método de Netwon

Si $g \in C^2$, $g(x^*) = 0$ y $g'(x^*)\neq 0$, si $x_0$ esta "suficientemente cerca de $x^*$" entonces NR converge `cuadraticamente` a $x^*$

Demo:
	![[FUO - Clase 2 - Algunos métodos básicos de optimización en R 2024-04-06 00.15.04.excalidraw]]