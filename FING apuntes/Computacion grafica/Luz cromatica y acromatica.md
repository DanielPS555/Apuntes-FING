### Motivacion:
- EL uso de sombras mejora notablemente la apariencia
- Es un tema complejo que mescla temas fisicos, artisticos y filosoficos
- Los objetos puede relejar luz o trasmitirla
- El color de un objeto depende de:
	- El propio ojeto
	- La luz incidente
	- El area que lo rodea
	- El sistema visual humano 

### Luz acromatica
- El unico atributo es la cantidad de luz
- La intensidad de mite en Wats (W)
- para el ojo humano, la diferencia de intensidades no se mide en resta, sino en la division. Por ejemplo Vemos una mayor diferencia entre 100 wats y 50 wats, que de 150 wats a 100 wats. Entonces para generar una distribucion uniforme de luz, tenemos que aumentar de forma exponencial la intensidad. 
- O sea que $l_1 = r.l_0$ y $l_{255} = r^{255}l_0 = 1$. O sea $r = (1/l_0)^{1/255}$ 
- Notar que el valor de $l_0$ depende del dispositivo. Ejemplo $l_0$ esta entre 1/40 y 1/200 para un CRT. 
- `Itervalo dinamico` = $1/l_0$ 
- Para no notar la diferencia entre los diferentes intensidades $r < 1.01$ 
- Notar que mientras mas grande es el intervalo dinamico, mayor debe ser el numero de intesndiades posibles. En particular para el valor de r antes mencionado, el `numero de intensaides requeridas` = $log_{1.01}(1/l_0)$ 

##### Aproximacion por medios tonos
- EN el caso de las impresoras no se pueden poner intensidades medias.
- Una posibilidad es poder variar el diámetro del punto
- Por lo general cuando se dibujan los puntos se lo hace inclinado.
- Cuando no se puede variar el diametro del punto, se puede aplicar la siguiente idea:
	- Dividir una region en varias areas, cada tonalidad es una distribución diferente de como pintar esas sub-areas 
	- ![[Pasted image 20240518040730.png]]
	- Se puede representar esta distreibucion con una unica matriz, por ejemplo la que vemos en la foto de arriba, si queremos dibujar la intensidad n, solo pintamos las entradas de la matriz que la intensidad deseada sea menor que n.
	- Cuando se eligue la distribucion, hay que tener ciertas cosas en cuenta:
		1. `Que no se generen efectos visuales artificalers`: Con esto nos referimos a que la agrupacion de estas distribuciones no genere efectos visuales. Por ejemplo:
			- ![[Pasted image 20240518041109.png]] Notar si se juntan varias de estas horizontalmente, mas que formar una region menos negra, lo que hacemos es formar una linea.
			- 
		2. `La secuencia debe ser creciente`: O sea, la secuencia de la intensidad siguiente debe incluir a la anterior
		3. Debe crecer hacia afuera desde el centro
		4. Deben estar agrupados
	- Notar que si a la hora de pintar un punto podríamos variar el tamaño del punto o hacer un punto grid, el numero de intensidades que podríamos crear aumentaría considerablemente. 
	- Notar que para una misma intensidad se puede conseguir con muchas convinaciones diferentes. Eso complica contar cuantas intensidades se pueden formar
		- ![[Pasted image 20240518042255.png]]

##### Método de difusión de errores
Cuando solo podemos utilizar un **pixel de representación** por cada **pixel de imagen**, se puede aplicar esta técnica. 
Cuando elegimos la intensidad, se genera un `error` entre el valor deseado y mostrado. 

El error puede ser positivo o negativo.

Ese error se **propaga** a los pixeles adyasentes como se muestra a continuacion:
![[Pasted image 20240518042750.png]]


## Luz cromatica

- `Tinte` = Distincion entre los colores
- `Saturacion` = Distancia entre un color y el gris de la misma intensidad
- `Claridad` = Es la intensidad percibida por un objeto reflejante
- `Brillantez` = Intensidad percibida por un objeto que emite luz
- Es para el ojo humano casi imposible distinguir entre la Claridad y Brillantez
- Para que un objeto pueda ser distingido, la longitud de onda debe ser MUCHO mas pequeña. Ese por ejemplo es el problema que teneos con los virus
- Nuestro ojo persive la luz a como la sumatoria de 3 otras ondas, una roja, verde y azul. 
- Es por eso que un color no tiene que ser una onda con una frecuencia pura, sino que puede ser variable pero la sumatoria resulrar en un mismo color. 
- Nuestro ojo persive la intensidad de forma despareja en el espectro de onda
- ![[Pasted image 20240518192927.png]]
- Notar que es por eso que no vemos las luces infrarojas
- Se dieron cuenta luego de varios experimentos, que con las combinaciones lineales de una luz roja, azul y verde NO podrian formar todo el espectro de onda.
- ![[Pasted image 20240518193304.png]]
- Hay algunos colores del espectro de onda que para formarlos presisamos una cantidad "negativa" de rojo
- Es por lo anterior que no podemos lograr todos los colores de la naturaleza
- 