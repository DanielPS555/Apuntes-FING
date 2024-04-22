#### Mallas poligonales
Es un conjunto de superficies planas, las cuales son limitadas por polígonos. 

Notar que esta malla no es mas que una colección de aristas, vertices y polígonos, que cumple: 
- Cada arista **a lo sumo** esta compartida por dos polígonos. 
- Los vertices **al menos** deben ser compartidos por dos aristas. 
- Todas las aristas son parte de aun

Puede haber varias `representaciones` para este tipo de malla, la cual se elige a conveniencia del programador. 

Puede haber varias representaciones dependiendo el uso, por ejemplo puede haber una representación para: Almacenamiento interno, almanceanmiento externo o modificación/creación interactiva. Notar que hay que tener en cuenta el Espacio y el Tiempo de las operaciones (Ej: Determinar aristas incidentes, dibujar, mover vértice de lugar, etc) para elegir las representación.


Algunas representaciones pueden ser:

- `Explicitas`: 
	Es una representación que es una lista de polígono es representa como una lista de coordenadas con sus vertices. 
	Los vertices en cada polígono están en orden
	Algunos problemas
	1. Desperdicio de espacio, se repite la coordenada de los vertices
	2. No hay forma de saber cuales son las aristas y los vertices compartidos, por lo que se pueden dibujar doble.
- `Apuntadores a una lista de vértices`:
	Aquí al inicio de la representación se tiene una lista con los vertices y las coordenadas de cada uno. 
	Luego cada polígono tiene una lista con los vertices.
	Notar que aquí hemos salvado espacio
	Es fácil modificar la obicacion de los vertices
	Aun podemos dibujar aristas duplicadas
- `Apuntadores a una lista de aristas`:
	Ahora tenemos al principio una lista de vertices, luego una lista con aristas con sus dos vertices, pero tambien con dos punteros a los dos posibles polígonos a los cuales puede pertenecer. 
	Luego los polígonos tiene una lista de aristas que lo componen.

Notar que aun quedan problemas, por ejemplo saber las aristas que inciden en un vertices, pero ta...


Para las mallas poligonales es importante encontrar la `normal` al plano. 
Para ello es necesario encontrar $A,B,C,D$ que resuelve la siguiente ecuación:
$$
Ax+By+Cz + D = 0
$$
Se pueden encontrar A B y C mediante el producto vectorial entre dos aristas:

$$
\bar{P_1P_2} \cdot \bar{P_1P_3}
$$

Y luego D es evaluar en uno de los puntos.

Hay otra forma mediante lo siguiente: 
![[Pasted image 20240414233952.png]]


![[Pasted image 20240414234005.png]]
