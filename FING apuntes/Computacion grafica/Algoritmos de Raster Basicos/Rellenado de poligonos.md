
Se utilizan las `lineas de rastreo` para rellenar el polígono. Donde las mismas se recorren llenando los pixeles que la conforman dentro del poligono.

![[Pasted image 20240313232514.png]]

**Importante**: Solo se dibujaran los puntos que se consideran `puntos interiores` del polígono.  


El rellenado se aplica utilizando los siguientes 3 pasos:
1. Encontrar las intersecciones de cada linea de rastreo con las aristas del polígono. 
2. Ordenar las intersecciones aumentado la coordenada x
3. Utilizando la regla de paridad, activar los pixeles entre pares de intersecciones dentro del polígono. 
		Observar que la regla de paridad comienza en par, cada vez que se encuentra una intercepción cambian de paridad. **Solo se pinta si la paridad es impar**

Hay 4 casos particulares a tener cuidado mientras se colocan los pixeles:

- `Caso 1: Intersepcion entre linea de rastero y arista resulta en numero fraccionario`
		Dado que nos estamos moviendo hacia la derecha en la linea de rastreo. Hay dos casos:
		- Si estamos dentro del poligono, redondeamos hacia abajo la coordenada fraccionaria (se define pixel interior)
		- Si estamos fuera del poligono, redondeamos hacia arriba la coordenada fraccionaria (se define pixel interior)
		![[Pasted image 20240313234346.png]]

- `Caso 2: Intercepcion en cordenada entreras (experesa en pixeles)`
		Dado un tramo de intersepciones:
		- Si el extremo **izquierdo** tiene coordenada entera, entonces lo definimos como interior
		- Si el extremo derecho tiene coordenada entera, entonces lo definimos como exterior.

- `Caso 3: Intercepciones de cordenadas enteras (experesas en pixeles) con vertices compartidos`
		En cada segmento de intercepciones se define un $y_{min}$ y un $y_{max}$. 
		En el calculo de paridad solo contamos los $y_{min}$ y no los $y_{max}$

- `Caso 4: Intercepcion de cordenadas entreras (experesa en pixeles) cuando definen una arista horizontal`
		En las aristas horizontales, no se considera para el calculo de la partidad ninguna de las dos intersepciones.


