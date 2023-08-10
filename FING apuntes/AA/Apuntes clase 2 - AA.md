PDF: [[Apuntes clase 2 - AA]]

# Aprendizaje Conceptual

## Def
Inferior un concepto a partir de un conjunto de entrenamiento

#### Def (hipótesis)
Nosotros elegimos como representar al concepto buscado. Por ejemplo un AND entre múltiples condiciones. 

A los posibles candidatos dentro de esa representación son conocidos como *hipótesis*

## Ejemplo
EJ: A partir de un conjunto de datos, cuando salva Pedro un examen

Buscamos inferir una funcion booleana $c: X \rightarrow \{0,1\}$ , donde $X$ es el conjunto de instancias. 
Notar que $c(x) = 1$ significa que todos pasan el examen

Se decide representar a la funcion $c$ de tal forma que el espacio $H$ de hipotesis tiene la forma: 
$$h:<Dedicación, Dificultad, Horario, Humedad, HumorDoc>$$

En este ejemplo, cada atributo es una restriccion que puede tomar 3 valores: 
- ? = todo 
- A = A como único elemento aceptado en la restricción
- ∅ = Ningún valor es aceptado

EJ: <Alta, ?, ?, ?, ?> son todas las personas que estudian mucho
