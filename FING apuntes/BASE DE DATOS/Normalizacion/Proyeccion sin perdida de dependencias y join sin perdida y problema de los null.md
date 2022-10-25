
## Definiciones 

### Esquema relacion universal R
$R=(A_1, A_2, ... , A_n)$  que contiene todos los atributos de la BD

### Descomposicion de R, D
$D=(R_1,R_2,...,R_m)$ que se obtiene mediante los algoritmos que realizan la descomposicion utilizado las dependencias funcionales.
Es importante verificar que $R_1 \cup R_2 \cup .... \cup R_m = R$   

### Proyeccion  de un conjunto de dependencias sobre una esquema de relacion 
Dado un conjunto de dfs F sobre R, $R_i$ un subconjunto de R, 
La *proyeccion* de F sobre $R_i$,  llamado $\pi_{R_i}(F)$ es el conjunto de las dfs X->Y en F+ tal que los atributos $X \cup Y$ esten todos en $R_i$. 

## Preservacion de dependencias 
Una descomposicion $D = (R_1, R_2, ...., R_m)$ de R preservas dependencias  respecto a F si se cumple que:
$( \pi_{R_1}(F)  \cup \pi_{R_2}(F) \cup ... \cup \pi_{R_m}(F))^{+} = F+$     

### Algoritmos asociados

![[Pasted image 20221016022340.png]]

## Join sin perdida
Una descomposicion $D=(R_1, R_2, ..., R_m)$ de R tiene la propiedad de *JSP* (Join sin perdida) respecto al conjunto de dfs F sobre T, si por cada instancia de relacion r de R que satisfaga F, se cumple lo siguiente:
$\pi_{R_1}(r) * \pi_{R_2}(r) * ... * \pi_{R_m}(r) = r$ (con " * "  join natural) 

### Propiedad
D = ($R_1$, $R_2$ ) de R tiene JSP respecto a F sobre R sii una de estas dos es cierta
- $(R_1 \cap R_2 \rightarrow R_1 - R_2) \in F+$ 
- $(R_1 \cap R_2 \rightarrow R_2 - R_1) \in F+$ 
Esto me quiere decir que con los atributos en comun (que es lo que va a hacer el join) puedo determinar una de las dos tablas perfectamente.

![[Pasted image 20221016024921.png]]


## Problema con los NULLs

Los nullos dos valores de dificil interpretacion. Deben ser utilizados unicamente en determinadas ocaciones. Es por eso que una opcion alternativa a su uso podria ser la siguiente: ![[Pasted image 20221016185730.png]]

Son tablas colgantes, el cuidado que hay que tener es cuando se elimina algo de la tabla original , tambien hay que eliminarlo de la tabla colgante.

Una cosa a tener en cuenta es que las primary key no pueden ser null