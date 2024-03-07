PDF: [[Apuntes clase 2 - AA]]

# Aprendizaje Conceptual
## Notación

- Dominio de instancias: $X$
- Función objetivo: $c: X \rightarrow \{0,1\}$
- Espacio de hipótesis: $H = \{h_0,h_1, ...\} , h_i:X \rightarrow \{0,1\}$
- Conjunto de Entrenamiento: $D = \{ ( x_0, c(x_0) ) ,  ... , ( x_n, c(x_n)) \}$ tal que $x \in X$

## Objetivo 
Buscamos un $h \in H$ tal que $\forall x \in X,$ $h(x) = c(x)$

Cuidado, nada nos garantiza que $c$ pertenezca al $H$ elegido 
## Defs
Inferior un concepto a partir de un conjunto de entrenamiento

#### Def (hipótesis)
Nosotros elegimos como representar al concepto buscado. Por ejemplo un AND entre múltiples condiciones. 

A los posibles candidatos dentro de esa representación son conocidos como *hipótesis*


#### Hipótesis mas general o igual
Sea $h_j$ y $h_k$ dos hipotesis boleanas
$h_j$ es mas general que $h_k$ ( $h_j \geq h_k$) sii $h_k(x) = 1 \rightarrow h_j(x) = 1$

#### Hipótesis mas especifica o igual
$h_j$ es mas espesifica que $h_k$ ( $h_j \leq h_k$)
	sii $h_j(x) = 1 \rightarrow h_k(x) = 1$ o  $h_k(x) = 0 \rightarrow h_j(x) = 0$

#### Hipotesis consistente
Una hipotesis es o no consistente con un conjunto de entrenamiento:

$$Consistente(h,D) = \forall(x,c(x)) \in D, h(x) = c(x)$$

#### Espacio de versiones
Es el conjunto de las hipotesis de $H$ que son consistentes, y por ende candidatas a ser el objetivo buscado.
$$VS_{H,D} = \{h \in H \text{ tal que } Consistente(h,D)\}$$
#### Limite general $G_{H,D}$
Es el conjunto de las hipotesis mas generales consistens de H.

$$G_{H,D} = \{ g \in H : consistente(g,D) \text{ y } (\nexists g' \in H, g' \geq g \text { y } consistente(g',D)) \}$$

#### Limite espesifico $S_{H,D}$
Es el conjunto de las hipótesis mas especificas consisten de H.

$$S_{H,D} = \{ s \in H : consistente(s,D) \text{ y } (\nexists s' \in H, s \geq s' \text { y } consistente(s',D)) \}$$

#### Sesgo inductivo
Es el conjunto mínimo de supuestos para asumir que la clasificación que nos da el modelo, es la clasificación correcta. 

"Mientras mas sesgo tiene mi algoritmo, mas logro generalizar, mas logro aprender. No tiene porque aprender lo correcto"

## Propiedades y teoremas

#### Hipotesis de Aprendizaje Inductivo
> Toda hipótesis que aproxime correctamente el concepto objetivo en un conjunto de ejemplos lo suficientemente grande, también lo hará sobre las instancias aun no observadas. 

#### Teorema de representacion del espacio de versiones
Se puede representar $VS_{H,D}$ sabiendo $G_{H,D}$ y $S_{H,D}$. 

$$VS_{H,D} = \{h \in H \text{ tal que } (\exists s \in S_{H,D}), (\exists g \in G_{H,D}), g \geq h \geq s\}$$

## Algoritmos

#### FIND-S
Se comienza con la hipótesis mas especifica y a medida que falla generalizo.
La idea es  obtener hipótesis mas especificas posibles, solo generalizando cuando es necesario. 

Notar que solo capto recuerdo las instancias, cuando estas tiene resultados positivos. 

```
h ≡ hipótesis más específica de H
Para cada instancia positiva x
	Para cada restricción r de h
		Si x no satisface r, sustituir r por una restricción más general que satisfaga x.
Devolver h
```


#### FIND-G
Análogo a FIND-S, pero se comienza con la mas general, y se va especificando hasta pasar por todas las instancias de $X$. 

#### Algoritmo List-Then-Eliminate
Lista todas las hipótesis, y aquellas que no sean compatibles las elimina. 

```
VS ≡ conjunto con TODAS las hipótesis.
Para cada ejemplo [x, c(x)]:
	Eliminar todas las h tq. h(x)≠c(x).
Devolver VS
```


#### Candidate-Elimination

```
S ≡ conjunto de hipótesis más específicas.
G ≡ conjunto de hipótesis más generales.
Para cada instancia x.
	Si x es un ejemplo positivo.
		Remover de G cualquier hipótesis inconsistente con x.
		Para cada hipótesis s de S, inconsistente con x.
			Cambiarla por todas las generalizaciones mínimas de s,
			consistentes con x, para las cuales haya una hipótesis en G
			más general que ellas.
			
			Remover de S toda hipótesis más general que otra hipótesis
			de S.
	
	Si x es un ejemplo negativo.
		Remover de S cualquier hipótesis inconsistente con x.
		Para cada hipótesis g de G, inconsistente con x.
			Cambiarla por todas las especializaciones mínimas de g,
			consistentes con x, para las cuales haya una hipótesis en S
			más específica que ellas.

			Remover de G toda hipótesis más específica que otra
			hipótesis de G.


```


### Ejemplo
EJ: A partir de un conjunto de datos, cuando salva Pedro un examen

Buscamos inferir una funcion booleana $c: X \rightarrow \{0,1\}$ , donde $X$ es el conjunto de instancias. 
Notar que $c(x) = 1$ significa que todos pasan el examen

Se decide representar a la funcion $c$ de tal forma que el espacio $H$ de hipotesis tiene la forma: 
$$h:<Dedicación, Dificultad, Horario, Humedad, HumorDoc>$$

En este ejemplo, cada atributo es una restriccion que puede tomar 3 valores: 
- ? = todo 
- A = A como único elemento aceptado en la restricción
- ∅ = Ningún valor es aceptado

Notar que bajo esta forma, tenemos $5.5.4.5.4$ hipótesis sintácticamente diferentes, pero sintácticamente son menos. En particular son todas las $<x,?,?,?,?>$ variando x de elemento y de posición, luego se le suma 1 que es el nulo. 

EJ: <Alta, ?, ?, ?, ?> son todas las personas que estudian mucho


