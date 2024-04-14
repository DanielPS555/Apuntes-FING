

### Definición (Convexidad de funciones)
Decimos que
$f: R^n \rightarrow R$ es convexa sii $\forall x,y \in R^n, \forall t\in [0,1], f(tx + (1-t)) \leq tf(x) + (1-t)f(y)$ 

![[FUO - Clase 3 - Convexidad 2024-04-06 01.49.55.excalidraw]]

> La cuerda esta por encima de la funcion 

Decimos que la `convexdidad es estrictra` cuando la desigualdad es estricta $\forall t \in (0,1)$. o sea no e t = 0 u 1.


### Prop
Si $f$ es convexa y diferenciable, entonces:
$$
\forall,x,z \in \mathbb{R}^n, f(z) \geq f(x) + <\nabla f(x), z- x>
$$
Demostracion:
	![[FUO - Clase 3 - Convexidad 2024-04-06 02.15.32.excalidraw]]
> La idea de esta propiedad es que el plano que forma un punto en el hiperpano esta por debajo de todos los puntos de la funcion. 

![[FUO - Clase 3 - Convexidad 2024-04-06 02.35.37.excalidraw]]

### Prop:
Si $f: R^n \rightarrow R$ tiene derivadas segundas a todos punta:
- Si $\nabla ^2 f(x) \geq 0 \forall x \Rightarrow$ f es convexa
- Si $\nabla ^2 f(x) > 0 \forall x \Rightarrow$ f es estrictamente convexa
Nota: $\nabla^2 f(x)$ es la matriz Hezziana.

### Definición
Decimos que $f$ es `concava` si $-f$ es convexa.


### Proposición
$f$ es convexa sii toda restricion a una recta es convexa.
> En el caso de $\mathbb{R}^n$ se puede ver como una función (ejemplo un cono) cuando es interceptado por un plano (restricción a una recta) forma una parabola, la cual es convexa. Por lo tanto el cono es convexa. 
	

### Proposición
$f$ es conexa sii es conveza $epi(f)$ (epigrafo) donde 
$$
epi(f) = \{(x,t) \in Dominio(f) \times \mathbb{R} \text{ tal que } t \geq f(x)\}
$$
Gráficamente es así
![[FUO - Clase 3 - Convexidad 2024-04-06 03.23.18.excalidraw]]

### Proposición
Si $f$ es convexa => todos los subconjuntos de nivel son convexos. Un conjunto de nivel es $C_k = \{x\in \mathbb{R}^n: f(x) \leq k\}$  

![[FUO - Clase 3 - Convexidad 2024-04-06 03.26.42.excalidraw]]

### Ejemplos de algunas funciones convexas
- Las `normas` son funciones convexas 
- $d(x) = min\{x_1,x_2,  .. , x_n\}$ es convexa
- $f(x) = log(det (x))$ es concava en $S_{++}^n = \{X \in \mathbb{R}^{n \times m} / X = X^T, X \text{ definida positiva}\}$ 



### Operaciones que perservas la convexidad
1. `Combinación lineal` de funciones convexas con `coeficientes no negativos`, es convexa. 
2. `Composicion` con un `mapa lineal`. O sea, si $f$ es convexa $\Rightarrow$ $f(Ax+b)$ es convexa 
3. `Maximo` y `supremo` de funciones convexas. O sea $f(x) = min\{f_1(x) , f_2(x)\}$


## Definicion
Un conjunto $C$ es convexo sii $tx + (1-t)y \in C$ $\forall x,y \in C, \forall t \in [0,1]$ 

Ejemplos: 
- Conjunto afiles (soluciones Ax= b)
- Bolas
- $S_{+}^n = \{X \in \mathbb{R}^{n \times m} / X = X^T, X \text{ semidefinida positiva}\}$ $ conjuntos de matrices semi definidas positivas 


