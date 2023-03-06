Es un nuevo paradicma de programacion

La computacion de resultados se hace mediante la *evaluacion de expreciones*. 
Durate la evaluacion, las definiciones actuan como *reglas de reduccion* que permiten *simplifcar las expreciones*. 

Cuando la exprecion llega a su resultado que no se puede reducir mas, se lo conoce como *forma normal* o *canonica*. 

La programacion funcional tiene la *Ausencia de efectos laterales*. Esto desencadena la siguiente propiedad

#### Propiedad
Dada una expresión `e` cualquiera se cumple que: todas las secuencias de reducci´on de `e` que terminen lo van a hacer en un mismo valor `v`.

Esta propiedad es caracteritica de los lenguajes de programacion funcional. 

En la mayoria de los lenguajes de programacion, el orden de las sentencias es fundamental. Esto se debe a que en los lenguajes imperativos, la base esencial es modificar valores alacenados en memoria. Mientras que en la PF *las variables denotan valores*.

Al igual que en las matemticas, en PF el valor retornado por una funcion solo depende de los valores dados como entrada. No hay variables globales que puedan modifcar el comportamiento de una funcion. 