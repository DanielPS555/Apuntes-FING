
## Principales componentes de un sistema grafico interactivo 
![[Pasted image 20240312225916.png]]
Nota: 
- Obvio que se le puede añadir un monton mas de perifericos diferentes 
- UCP = CPU




## Tecnología de Impresoras

Las impresoras puede utilizar diferentes `distancias entre pixeles`, por ejemplos puede hacer que la distancia entre los centros de dos pixeles sea de un pixel como de menos. 

En las impresoras no existe una relacion definida entre el tamaño de un punto y la distancia entre ellos. 

Algunos ejemplos: 
![[Pasted image 20240312233058.png]]

Notemos que aquí que el problema del `Antialiasing` (escalonamiento) queda disminuido. 

Notar que también hay una relation con la `distribucion de intensidad`. Esta lo que significa es como se va a distribuir a su alrededor la tinta cuando es aplicada a un punto. 

![[Pasted image 20240312233652.png]]

Si la distribución es baja como en el punto "a" se consigue mayor separación y definición del punto en la distribución en "b", mientras que en el caso "d" quedan superpuestos y por ende continuo.


##### Algunas definiciones importantes: 
- `Tamaño del punto`: Es el diámetro del punto creado. 
- `Capacidad de dirreccionamiento`: Numero de puntos por pulgada (que tiene diferente coordenadas)
- `Resolucion`: Se refiere a que tan chico puede ser el espacio que permite distinguir una linea negra de una linea blanca adyacentes. Por ejemplo si puedo poner en una pulgada 40 lineas negras y 40 lineas blancas 

##### Manejo de colores impresora
Se utiliza los colores "Cyan, Amarillo y Magenta". A estos se los denomina `colores primarios sustractivos`. Son sustractivos ya que añadir estos colores lo que se hace sustraer parte del color que refleja la hola, mientras que en la pantalla es al reeves.

![[Pasted image 20240313004740.png]]

Notar que la mezcla entre Amarillo, Cyan y Magenta es negro, o sea, ausencia de color. 


Otro factor a tener en cuenta es que las impresoras de tinta o laser no pueden formar el color que quieran en cada punto, sino que puede ser solo 8 (principales + combinaciones + blanco (nada)) . Entonces para formar otros colores mas complejos utiliza el concepto de `Dithering`. 

El concepto `Dithering` es imprimir colores diferentes en puntos muy cercanos para que sea el ojo quien los mescle y pueda formar nuevas tonalidades. Por ejemplo el gris es una mescla entre no imprimir nada e imprimir el negro, por lo tanto en una region gris si hacemos zoom veremos cuadrados negros y blancos muy cercanos. Notar que para poder obtener esto es fundamental tener **una resolucion muy superior a la de un monitor**. 

![[Pasted image 20240313200832.png]]

##### Tipos de dispositivos Impresion


- Dispositivos de barrido
	- ``Impresoras de matrices de punto``: Cabel con una serie de agujas, usa varias tintas.
	- ``Impresoras a chorro de tienta``: lanza tinta por boquillas. Se puede **lograr puntos de tamaño variable**
	- `Impresoras de tranferencia de tintes por sublimacion termica`. Permite generar 256 intensidades diferentes de C,M, Y. Se consigue una gran calidad
- Dispositivo laser
	- `Impresora laser`: El tambor y el toner (tinta) tiene carga opuesta. El lazer tiene la propiedad de descargar la zona del tambor que quiera. El tambor adiere el toner en las zonas cargadas y lo adiere al papel. Luego se calienta para fijar el toner en la hoja de papel.  
- Dispositivos vectoriales
	- `Graficador de pluma (plotter)`: Desliza una pluma sobre una hoja de papel, permitiendo formar fácilmente vectores. 


## Tecnologías de monitor.
[Mirar PDF]

## Dispositivos de entrada
[Mirar PDF]

## Vectorización
Tambien llamado `procesamiento de imagenes`. Es el proceso de reconocer los elementos que consiste una imagen. 
Es una `tarea de software` luego de capturada la imagen.

Algunos de los pasos son:
- Detection de valores limites.
- Extraction de características.
- Reconocimiento de patrones via reconocimiento de primitivas simples.