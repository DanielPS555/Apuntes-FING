# Indice de convexidad 
1. Objetivos
	1. Terminologia
	2. Estudidar caracteristicas e conjuntos y fines comvexas 
2. Motivacion
		1. ¿Porque la convexdiad se mantiene?
		2. ¿Porque cuando tenemos conjuntos y fines convezas que podemos identificar optimos globales? [clase que viene]
3. Definicionesunciones convexas en los $R$ 
4. 
5. Definicionesunciones convexas en los $R^n$

# Objetivos
## Terminologia



# Motivacion

## Porque se mantiene
Sucede que se puede construir conjutos y funciones convexas mas complejas en base a funcionesy conjuntos convexas mas simples  

# Definiciones 

#### Conjunto convexo
*Definicion intuitiva* 
Un conjunto C en $R^n$ se dice convexo si contiene todos los segmentos de recta entre puntos en C. 

*Definicion formal*
C en $R^n$ es un conjunto convexo si $\forall x,y \in C$ , $\lambda \in [0,1]$ $(1-\lambda).x + \lambda.y \in C$ 

![[Clase 1-3 -- Convexidad 2023-03-02 01.20.33.excalidraw]]


#### Funcion convexa
*Definicion intuitiva*
Una funcion `f` en un conjunto convexto C es convexa si esta por debajo de sus cuerdas. 

![[Drawing 2023-03-02 01.11.50.excalidraw]]

*Definicion formal*
Sea $f : C \rightarrow R$ es conxea si 
$\forall x,y \in C$ y $\lambda \in [0,1]$  $f[(1-\lambda)x + \lambday ] \leq (1-\lambda).f(x) + \lambda.f(y)$  

# Teoremas

#### Teorema 1
Sea los conjuntos `C` y `D` convexsos, y $\alpha \in \mathbb{R}$. 
Entonces los siguientes conjuntos cambien son conexsos:
1. $\alpha C = \{ \alpha x : x \in C \}$ 
2. $C \cap D$ 
3. $C + D$

##### Demo
Buscamos que se cumpla la def de conjunto conexo. 
Osea $\forall x, y \in \alpha C$, $\forall \lambda \in [0,1]$,  $(1 - \lambda)x + \lambda y \in \alpha C$

Tomemos $x, y \in \alpha C$ cualquiera
$\Rightarrow x_1, y_1 \in C$ tal que $x = \alpha x_1$ y $y = \alpha y_1$ 
Como C es convexo 
	$\Rightarrow$ $\forall \lambda \in [0,1]$ $(1 - \lambda) x_1 + \lambda y_1 \in C$ 
	$\Rightarrow$ $\alpha (( 1 - \lambda )x_1 + \lambda y_1) \in \alpha C$ 
	$\Rightarrow$ $(1-\lambda)x + \lambda y \in \alpha C$    #

#### Teorema 2
Sean `f` y `g` funciones conexas en el conjunto convexto C y $\alpha \geq 0$

Entonces las siguientes funciones con conexas
1. $f + g$
2. $\alpha f$ 

#### Teorema 3
Sea $f : C \rightarrow \mathbb{R}$. 

$f$ es conexa sii $\forall x, y \in C$,  $\lambda \leq 0$ o $\lambda \geq 1$ $f[ (1-\lambda)x + \lambda y ] \geq (1 - \lambda) f(x) + \lambda f(y)$ 

En otras palabras, a la isquierda de x y a la derecha de y, la funcion este por ensima de la cuerda. 


#### Teorema 4
Sea $f : I \rightarrow \mathbb{R}$ en un intervalo $I \subset \mathbb{R}$ es conexo si 

$\forall x,y \in I$ se cumple que $\frac{f(y) - f(x)}{y-x} \geq f`(x)$
![[Clase 1-3 -- Convexidad 2023-03-02 01.57.25.excalidraw]]


#### Teorema 5
Sea $f:I \rightarrow \mathbb{R}$ diferenciable es convexa en $I$ sii $f'$ no decreciente 

**Importante**: Ninguna de estos teoremas se usan para una mierda menos el 1º, los dos que importan son los siguientes: 


#### Teorema 6
Una funcion 2 veces diferenciable $f : I \rightarrow \mathbb{R}$ 
$\Rightarrow$ f convezo en $I$ si $f'' \geq 0$ 

![[Clase 1-3 -- Convexidad 2023-03-02 02.07.20.excalidraw]]


#### Teorema 7
Sea $f : I \rightarrow \mathbb{R}^n$ dos veces diferenciables. 

$f$ es convenxa si $H$ (matriz hessiana) es semidefinida positiva.

Recordar que:

- Una matriz es semidefinida positiva sii $\forall Y \in \mathbb{R}^n$, $Y^T H Y \geq 0$ 

- $$\begin{equation}
H = 
\begin{pmatrix}

\frac{\partial^2 f}{\partial x^2} & \frac{\partial^2 f}{\partial y \partial x} \\  
\frac{\partial^2 f}{\partial x \partial y} & \frac{\partial^2 f}{\partial y^2} \\  

\end{pmatrix}

\end{equation}$$
Un ejemplo: 

![[Clase 1-3 -- Convexidad 2023-03-01 23.50.27.excalidraw]]