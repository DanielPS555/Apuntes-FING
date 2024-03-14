Dado un area de visualization, se utiliza el algoritmo de recorte de lineas de `Cohen-Sutherland` para descartar las lineas fuera de esta area y recortar los segmentos que se encuentran parcialmente en el. 

![[Pasted image 20240314001906.png]]

Se divide la cuatro regiones la superfice de la siguiente forma:

![[Pasted image 20240314002052.png]]

Notar que si:
- Se encuentra prendido el `1º bit` es porque esta a la ``isquierda`` del area de visualización.
- Se encuentra prendido el `2º bit` es porque esta a la ``debajo`` del area de visualización.
- Se encuentra prendido el `3º bit` es porque esta a la ``derecha`` del area de visualización.
- Se encuentra prendido el `4º bit` es porque esta a la ``arriba`` area de visualización.

**Propiedad**: 
	Si el AND entre los Codigo de las regiones de dos vertices es diferente de cero. entonces se rechaza la Linea definida por esas dos vertices. 


Si el AND es 0000 no se la puede rechazar, pero tampoco sabemos si esta completamente afuera o solo parte. Para ello se divide la Linea en 2 partes utilizando como divisor la intersection de la arista con los divisores de las regiones. Sabemos que divisor de region por el codigo del vertice.

La division va a generar que al menos una de las dos partes se descarte, pero se pueden descartar las dos a veces.