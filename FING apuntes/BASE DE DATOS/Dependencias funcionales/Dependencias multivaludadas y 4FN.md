La idea es representar una dependencia de un atributo con dos atributos independientes. 

## Idea intuitiva 
> Si se tienen 2 o más atributos que tienen más de un valor asociado con determinado objeto y que son independientes entre sí, se tendrán que repetir todos los valores de uno de los atributos con cada valor del otro atributo manteniendo la misma referencia para los objetos, para que las tuplas de la relación sigan siendo consistentes. Esta restricción se especifica con una dependencia multivaluada.

## Definicion formal
Una *dmv X ->> Y* espesificada sobre un er R (con un sobconjunto X e Y) espesifica la siguiente restriccion sobre R.
Si $\exists t_1, t_2 \in R$ donde $t_1(X) = t_2(X)$ entonces se debe cumplir lo siguiente: 
- $t_1(X)=t_2(X)=t_3(X)=t_4(X)$
- $t_1(Y)=t_3(Y)$ y $t_2(Y)=t_4(Y)$ 
- $t_1[R-(XY)] = t_4[R-(XY)]$ y $t_2[R-(XY)] = t_3[R-(XY)]$

## Dmv trivial 
Una dmv x->> Y es trivial si sucede alguna de estas dos cosas
- Y es un subconjunto de X
- X $\cup$ Y  = R





*Observacion*, 
- Los atributos multievualuados generan dmv, aunque si las separamos en otras tabla (en el pasaje al mer) terminan siendo triviales, por lo que se quitan.
- Si nos quedan dmv en las dependencias multiples, deberia haber sido dos relaciones distintas 