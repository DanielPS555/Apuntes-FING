## Indice 
- Intro
- Ej Terminologia, Generalizacion
- Clase de problemas 
- El objetivo 



# Introduccion
Optimizar = Hacer lo mejor posible 
- *hacer*: Buena decision
- *algo* = problema (queremos tomar una desicion hacerca de un problema en particular)
- *lo mejor*= minimizar o maximizar
- *posible*=limitaciones (EJ: Limitacion de mano de obra, limitaciones con maquinaria)

## Tipo de desiciones
- *Estategicas*: Son desiciones a largo plazo. EJ: Donde ubico una fabrica 
- *Tacticas*:  Hay un plazo pero es corto 
- *Operativas*: Se toma la decicision inmediata. Es por ejemplo como se realiza la operacion.


A la solucion que llegamos hay que evaluarla. Pero la solucion no es para la realidad, pero no para el problema

Hay problemas que estan bien formados y se pueden llevar a un modelo matemtiatico. Hay otros los cuales no, por ejemplo mejorar la educacuion, eso es porque no sabemos el problema. 

Soft IIO: Se utiliza para problemas no tambien formados, por ejemplo temas militares. 

PCM: En esa rama se estudian problemas que en realidad no estamos seguros que sean un problema, lo que tenemos son persepciones de las personas. Se usan en otros tipos de modelos.

Modelo: es una simplificacion selectiva de la realidad 


## Terminologia, Generalizacion

Tenemos una lata de radio r y altura h. 

Osea:
Queremos minimizar el area de la lata y maximizano su 

min $A = 2\Pi r^2 + 2\Pi r h$
Sugeto a: 
$V = \Pi r^2 h = 1$  con  $r, h > 0$ 

Tambien podria ser un problema de esta forma. Mucho mas formal : 

$min f(x, x_2)$
Sugeto a 
	$g_i(x_1,x_2) \geq b$
	$h_k(x_1, x_2 = 0$
	$x \in X$

### Terminologia
- Lo queson las variables que determinan  queremos min/max se denomica *funcion objetivo*. En el ejemplo anterior es `f`. En el caso del ejemplo de la lata era `A`.
- $(x_1, x_2, ... , x_n)$ se denomina *variable de decision*, el valor de estas variables son las desiciones que vamos a tomar. 
- `g` y `h` se denominan *restricciones*. Son las limitaciones que se tienen 
- $X$ es el *dominio*
- dominio + Restricciones = *Region factible*. Las unidades variables tiene que estar dentro de esta region.

## Clases de problemas
Se clasifican segun la funcion objetivo, el dominio y las limitaciones.

- Si `f` y `g` son linales en X, con $x \geq 0$ Es *Programacion lineal*. 
- Si f y/o g son no lineales en x $\rightarrow$ *Programacion no lineal*
- Si `f` y `g` son lineales en x y si algun componente de `x` es $\geq$
0 y enterquesono $\rightarrow$ *Progrmacion lineal entera*. 



Un problema posible (que es NP hard) seria meter items en la mochila, que esta acotada a 12kg, pero maximizando el valor. 
i = 1, 2, 3, 4
$V_i$= 2,4,6,8
$P_i$= 2, 3, 4, 5

Vamos a tomar la relacion $V / P$. 
el Cual es (en orden de i) 1.6, 1.5, 1.3 y 1. Por lo que los voy ingresando en ese orden hasta que ya no pueda poner mas. 

En ese caso elegimos el i = 2, 3 y 4. Pero esta forma no usa los metodos del curso.Ya que etse metodo no escala.

El modelo correcto seria 

$max$ $\sum_{i=1,..,4} v_i x_i$
	Sa 
		$\sum_{i=1,..,4} p_i x_i$
		$x \in \{ 0,1 \}$



## Objetivos en otimizacion
1. Terminologia
2. Aprender metodos para determinar soluciones optima (aun no se definicio que es una solucion optima)
3. Transaciom entre modelo verbal y matematica 

## Contenido
Para los objetivos, la caja de heramientas es:
1. Convexividad
2. Optimo locales y golbales (KKT)
3. Relataciones
4. Dualidad
5. programacion lineal, metodo simplex


