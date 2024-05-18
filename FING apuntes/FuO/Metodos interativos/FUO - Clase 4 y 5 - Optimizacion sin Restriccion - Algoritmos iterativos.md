
Vamos a construir una sucession $x_1, x_2, ... x_n$ con la esperanza de tender a un punto que sea solucion (o sea que tenga gradiente nulo).

## Definicion (metodo desenso)
Decimos que un metodo es un `desenso` si $f(x_{n+1}) \leq f(x_i)$ 


## Continuamos avanzando con metodos...
Veamos método de la forma $x_{k+1} = x_k + \alpha_k. d_k$ .  

Donde:
- $d_k \in \mathbb{R}^n$ es una dirrecion
- $\alpha_k \in \mathbb{R}^+$ rs un peso

Notar que cuando $\langle \nabla f(x_k), d_k\rangle < 0$ decimos que es un `metodo de gradiente`. 
Ademas a una dirección $d_k$ que cumpla con lo anterior se lo llama `dirrecion de desenso`. 

Obs: $\langle f(x_k), d_k\rangle$ es la derivada de $f$ en la dirreción $d_k$.

![[FUO - Clase 4 - Optimizacion sin Restriccion - Algoritmos iterativos 2024-04-10 01.53.39.excalidraw]]



Notar que $\exists \delta < 0$ tal que $f(x_k + \alpha d_k) < f(x_i)$ para $\alpha \in (0,d)$ notar que ese $\alpha$ es parte de los valor que buscamos para nuestro método.


## Inicio de la creación del algoritmo del método

Inicializamos en $x_0$
Repetimos
	Elegir dirrecion $d_k$
	Elegir un paso $\alpha_k$
	$x_{k+1} = x_k + \alpha_k  d_k$
Hasta

Comenzamos a resolver algunas duda:
1) ¿Como elegimos en d_i?
		Vamos a tomar la dirrecion $d_k$ de esta forma:
			$d_k = - D_k \nabla f(x_k)$ con $D_k \in S^n_{++}$
		Notar que si se define de esta forma, entonces para forzar a que $d_k$ sea una dirreción de descenso, podemos hacer lo siguiente:
			$\langle \nabla f(x_k), d_k \rangle < 0$	
			$\nabla f(x_k) ^T D_k \nabla f(x_k) > 0$ O 
			O sea tengo que elegir un D_k que sea definida positiva para garantizar que $d_k$ sea dirrecion de denso. 
		Hay varios ejemplos que cumplen eso:
			- $D_k$ = $Id$ (método llamado steepest descat). 			$$x_{k+1} = x_k - \alpha_k \nabla f(x_k)$$
				Notar que parece ser lo mas logico. Pero puede tener algunos problemas. 
				En una función cuadrática del estilo $f(x,y) = 1000x² + y²$ hace zig zag a medida que va bajando. Lo mejor que podes tomar en el paso a paso vas a hacer zig zag de 90º
			- D = $(\nabla ^2 f(x_k)) ^{-1}$ (Método de Newton) Sale del Taylor de orden 2. 
				$$x_{k+1} = x_k - \alpha_k (\nabla ^2 f(x_k))^{-1}\nabla f (x_k)$$
				Notar que eso se deduce de minimizar lo siguiente:
				![[FUO - Clase 4 - Optimizacion sin Restriccion - Algoritmos iterativos 2024-04-10 02.55.08.excalidraw]]Notar que eso lo que hace es compensar la deformación de la función.  
				Newton `es lo mejor como metodo`, pero es caro en cuanto a invertir y a calcular la derivada segunda.
			- D = $$
\begin{pmatrix}
d_{k_1} &  &  &  \\
 & d_{k_2} &  &  \\
 &  & ... &  \\
 &  &  & d_{k_n}
\end{pmatrix}
$$ con $d_{k_i} = (\frac{\partial^2f(x_k)}{\partial x^2_i})^{-1}$ 
				Notemos que este metodo es `casi como un newton`, pero mucho mucho mas eficiente en su computo (tanto invertir como el numero de deriadas)

2) ¿Que paso elegimos?
	- `Line search`:  Buscamos el $\alpha$ tal que $d(x_k + \alpha_k d_k) = min_{\alpha > 0} \text{ } f(x_k + \alpha d_k)$. Notemos que esto es un problema de minimizacion de una variable en $\mathbb{R}$, por lo tanto ya tenemos metodos para resolvera.
			hay Veces que si conocemos la funcion, podemos calcular esto cerrado en una hoja y hardcodear en el codigo la eleccion de $\alpha$ 
	- `Limited line Search`: Es lo mismo, pero acotamos la búsqueda de $\alpha$ hasta un $s$. Con ese limite para el $\alpha$ entre $(0,s]$ se pueden aplicar métodos como el Golden Search. 
	- `Armijo`
	- `Paso fijo`: Fijar el $\alpha_k$ a un valor fijo que no cambia.
	- `Paso decreciente`: El $\alpha_k$ va disminuyendo. En particular la suceccion debe cumplir lo siguiente: $\alpha_k \rightarrow_{k \rightarrow  \infty } 0$ y $\sum \alpha_k = \infty$.
		Ej: $\alpha=\frac{1}{k}$ 
3) Hasta cuando seguimos iterando?
		Recordemos que estaos buscando $x$ tal que $\nabla f(x) = 0$. Desarrollemos criterios de parada en base a eso:
	- $|| \nabla f(x_k) || < \epsilon$ Notemos que esto es lo mas inmediato
	- $\frac{|| \nabla f(x_k) ||}{|| \nabla f(x_0) ||} < \epsilon$ Notar que es lo mismo que lo anterior pero normalizado con respecto al punto inicial.
	- $|f(x_{k+1}) - f(x_k)|$ No es tan buen indicador como los anteriores.

		
		
		
	
## Proposición
Si las direcciones $d_k$ son de descenso y los $\alpha_k$ son elegidos según Armijo
Entonces :todos los puntos de acumulacion de $x_k$ son estacionarios (puntos criticos).

Observación: `Funciona tambien para paso decresente y paso fijo en cierto entorno`


## Caso particular: Convergencia del metodo de desens por gradiente con paso fijo

Para probar esto vamos a suponer que la funcion $g(x) = x - \alpha \nabla f(x)$ es una contraccion. 
En otras palabras: $||g(x), g(y)|| \leq  \beta || x-y ||$ con $\beta \in [0,1)$

Notar que si $x^*$ es un minimo local, entonces $g(x^*) = x^*$ 

En ese caso podemos observar que: 

![[FUO - Clase 4 y 5 - Optimizacion sin Restriccion - Algoritmos iterativos 2024-04-14 01.22.07.excalidraw]]



## Observar (¿Como se aplica esto?)
Si $f \in C^2$ , que sea una contracción es pedir que locamente f sea convexa. 