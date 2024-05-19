- Hay dos enfoques:
	- `Precision de imagenes`: Determina el objeto mas cercano al observar que es atravesado por el rayo proyectado a travez del pixel
	- `Precision de objeto`: 



- Coherencia
- Tranformacion en persepctiva
- Extension y volumenes acotantes: 
	- Si la acotación nos dice que dos elementos no se superponen, entonces puedo ahorrar todos los cálculos de superposición precisos. Si hay superposición, entonces hay que hacer los cálculos finos.  
	- No tiene porque usarse necesariamente una caja, por ejemplo en el siguientes caso seria una mala elección una caja: 
	- ![[Pasted image 20240519042422.png]]
	- Por ejemplo se pueden usar eferas, o "lozas". 
	- La elección es un trade-off entre la simplicidad de trabajar con el objeto envolvente y que tan precisamente lo envuelve. 
	- Se utiliza la siguiente formula para ello:$$T = bB + oO$$
	- T = Costo de los test de intercepción, dentro de las opciones para elegir la figura envolvente, debemos elegir la que nos de el $T$ mas bajo. 
	- b = Numero de veces que se debera realizar el "test" de intersepcion con el objeto envolvente. Mientras Por ejemplo en la figura de arriba, en la caja mas acotada (la diagonal) se debería hacer dos veces. 
	- B = Cual es el costo para poder calcular el test de intersección entre dos volúmenes acotantes.
	- o = Si hay intercepción entre las cajas, $o$ es el numero de veces que el objeto es testeado
	- $O$ = El costo de calcular la intercepción entre dos objetos. 
	- Notar que hay un trade-off entre $bB$ y $oO$, ya que si es fácil el calculo de los cuerpos envolventes, vamos a tener que pagar el costo sobre el calculo de la intercepción del cuerpo entero. 
- Eliminacion de caras posteriores:
	- Solo se debe aplicar para objetos cerrados. 
	- No consideramos todas las superfices donde el angulo entre la normal y el rayo camara pixel sea mayor a 90º 
	- ![[Pasted image 20240519045141.png]]
- Particion espacial: No lo entendi muy bien
- Jerarquia: Se va considerando la intersepcion en grupos cada vez mas pequeños de forma jerarquia. 
	- Por ejemplo, si tenemos un edificio, si los edificios tiene superposicion no evaluo mas, si si lo tiene empiezo a ver cada piso del edificio, y si no lo tienen no superposicion no sigo. Y asi con el edificio, piso, apatamento, etc...



## Algoritmos

#### z-buffer
- Hoy en dia es la mas usada 
- Es la fuerza de mas fuerza bruta, pero las graficar logran hacerlo viable
- Utilizando la `tranformacion de perspectiva` cuando se hacer el render de la linea de barrido, se registra el *z*, y solo se añade al buffer de la imagen el que tenga el mayor *z*  observar que con los volumen de vista canonica, se trabaja con z negativos. 
- los $z_i$ se pueden calcular de forma incremental dentro de un poligono. 
#### Linea de barrido
