# Definiciones previas

## Atributos Primos
Un atributo del esquema R es *primo* si es miembro de alguna clave R

## Dependencia funcional Total
X -> Y es una *dependencia funcional total* si la eliminacion de cualquier atributo de X hace que la df deje de ser verdadera. 

## Dependencia Parcial
X -> Y es una *dependencia funcional parcial* si es posible eliminar un atributo de X y  la df sigue siendo valida. 

## Dependencia funcional transitiva
Una df X->Y es un  er R es una df *transitiva* si existe una conjunto de atributos Z que no sea un subconjunto de una clave de R, y que se cumple que X->Z y Z->Y


# Formas normales

## Primer forma normal
>  Los dominios de todos los atributos son *atomicos* (no multivalorados ni compuestos)

## Segunda forma normal 
>Un relacion R esta en 2NF si ningun atributo no primo depende parcialmente de cualquier clave de R

En palabras mas faciles, todo atributo no primo debe depender totalmente de cualquier clave de R.

Esto lo que nos permite es eliminar redundancia de las tablas.
Ej: 
![[Pasted image 20221016005146.png]]
![[Pasted image 20221016005207.png]]

## Tercer forma Normal 

Una er R esta en 3NF si esta en 2NF y ningun atributo no primo de R depende transitivamente de una clave de R.

**Definicio equivalente:** Una er R esta en 3NF si siempre que una df X->A se cumple en R una de las dos sigientes opciones 
1. X es una superclave de R
2. A es un atributo primo de R

![[Pasted image 20221016012517.png]]


## Forma Boyce-Codd (BCNF)

Una er R esta en BCNF si, siempre que una df X->A se cumple en R, entonces X es una super-clave en R.

**¿Cuando estoy en 3NF y no en BCNF?** Deberia quedar como X->A con X no super-clave y A primo-