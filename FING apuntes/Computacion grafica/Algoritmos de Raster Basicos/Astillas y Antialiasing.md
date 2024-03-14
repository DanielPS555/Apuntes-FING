Cuando los polígonos tiene aristas muy cercanas, se puede producit que haya lineas de rastreo sin pintar. 

![[Pasted image 20240314004349.png]]

Una posible solucion es poder pintar pixeles en intensisdades intermedias entre el totalmente apagado y ensensido. 


## Eliminación de artefactos de discretizacion (Antialiasing)

Puede ocurrir el fenómeno de "Serramiento" o "escalonamiento" a la hora de discretizar figuras, como se ve a continuacion. 
![[Pasted image 20240314004732.png]]

Hay multiples soluciones a este problema

##### Solución 1: Aumentar la resolución. 
Si aumentamos la resolucion se notara menos el problema, pero aun no desaparece. Ademas es muy poco escalable la solución.

##### Solución 2: Muestreo de area no ponderada 
Se le asigna un grosor a la linea. Los pixeles tiene también un area que al encenderse iluminan. El porcentaje del area del pixel que este cubierta por la linea sera la intensidad que tomara el pixel. 

![[Pasted image 20240314005148.png]]

![[Pasted image 20240314005142.png]]


Notar que para el calculo de la intensidad del pixel solo nos importa la region de superposición, no que region es la que esta siendo superpuesta, es por eso que se le dice `no ponderado`. 

Se puede ver la función de ponderación como una caja de volumen 1, como en la siguiente figura. 

![[Pasted image 20240314005332.png]]
El gris es la tonalidad del pixel


##### Solución 3: Muestreo por area ponderada 
La intensidad del pixel estará dada por la distancia del area superpuesta y el centro del pixel. Es por eso que se pondera de diferente forma el area superpuesta para el calculo de la tonalidad del pixel. 

Por ejemplo se puede utilizar una función e cono para representar la ponderación. Hay funciones mas optima, pero la función del cono es muy simple. 

![[Pasted image 20240314005702.png]]