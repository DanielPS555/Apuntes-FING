- Vamos a ver tecnicas de ray traising contra los algoritmos raster que son mas rapidos de procesar. 
- Notemos qu cuando una luz choca contra una superfice puede pasar dos cosas:
	- Refractado: Cambia su angulo, pero atraviesa la superficie
	- Reflexión: Rebota en la superfice. 
- Notar que cuando pasamos de un material a otro, ambos materiales tiene (aproximadamente, no ser puede cuantificar solo en un numero) `"Indices de fraccion"`. 
- ![[Pasted image 20240521000032.png]]
- Cuando el angulo de incidencia es mayor que $arcsin(n2/n1)$, entonces ocurre la reflexión. 



## Algunos problemas
- Funciona bien cuando la superfice tiene una reflexion perfectamente especular o perfectamente difusa. Puede ser que queramos que la reflexion de luz no sea un "espejo" 
- hay que tener cuidado con cuestiones numericas, cuando se calcula una intersepcion, estar seguro (restando un epsilon) que estamos trabajando con un punto del borde (un poco exterior) del objeto. 
- 