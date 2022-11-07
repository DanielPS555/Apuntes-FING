Esto se da dentro del *geneador de planes logicos*
La idea es cambiar la consulta original por otra equivalentes que minimize los resultados intermedios durante el proceso. Por ejemplo podria ser aplicar primeros los operadores de seleccion que elimina tuplas. 

La idea va a ser aplicar equivalencias en los operadores de algebra para aplicar selecciones y proyecciones lo antes posible. 

Este proceso puede generar multiples alternativas. 

## Reglas de equivalencia de expreciones
![[Pasted image 20221102225646.png]]

``Observaciones``:
- La asociatica del join funciona con dos condiciones distintas en el join

![[Pasted image 20221102233520.png]]

Hay que aplicar los siguientes pasos para obtener el plan logico optimizado: 
![[Pasted image 20221102233854.png]]