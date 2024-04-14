
## Primera definición

Un problema de optimizacion convexa según Boid es de la siguiente forma: 

![[FUO - Clase 3- Problema de optimizacion convexa 2024-04-06 04.12.34.excalidraw]]

Notemos que tenemos 
- Una función objetivo convexa
- Restricciones de desigualdades de funciones convexas
- Restricciones de igualdad de funciones lineales


## Segunda definición
Otra forma de escribirlo es la siguiente forma: 

![[FUO - Clase 3- Problema de optimizacion convexa 2024-04-06 04.17.47.excalidraw]]

Observar que son equivalentes las dos formas. Ya que cada una de las restricciones de la primera definición o son un conjunto conexo, o es lineal. Por lo tanto la intersecciones de estos conjuntos termina siendo convexo.


### Proposición (`Super importante`)
En un problema de optimizacion convexa un mínimo local es un mínimo global.

> `Comentario de color`
> Existen librerías que resuelven cualquier problema de optimizacion convexa. En particular hay un paquete llamado `cvx` el cual en matlab (ni idea den python) lo resuelve. 