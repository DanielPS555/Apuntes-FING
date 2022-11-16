Tanto la deteccion como la correcion de errores, son servicios que son usualmente provistos por la capa de enlase. 

Si un emisor tiene que enviar D bits a un receptor, se complementan con otros bit de deteccion y correcion de errores (*EDC*). Tanto los D como los EDC son enviados al receptor. 
**Importante:** No solamente el datagrama esta cuvierto por estos bits, sino que tambien la cabecera de la capa de enlase. 

Estas tecnicas no garantizan que vayan a detectar el error, osea pueden exitir *errores de bit no detectados*. La idea es buscar un esquema que haga que esta pobilidad sea baja. Aunque mientras mas complejo el sistema, mas recursos adicionales seran necesarios. 

Hay multiples tecnicas: 

## Comprobacion de bit de paridad 
Es una de las tecnicas mas simples: 
Se añade un bit mas al final de los d bit enviados. Hay dos esquemas de partidad, en esquema de partidad par y el esquema de paridad impar. 
En el caso del esquema de partidad par se eligue el bit de paridad de tal forma que los d + 1 bit hagan que la cantidad de 1s sea par. Mientras que si el esquema es de paridad impar, se configura el bit de paridad para que la cantidad de 1 en los d + 1 bit sean impar. 

*Importante*
- Este tipo de comprobacion solo puede detectar cuando se produjo un numero impar de errores de bit. 
- Es un buen sistema si la posibilidad de error es baja y ademas la posibilidad de error entre los bit es independiente. Pero por lo general los error ocurren en *rafaga* . 

Tambien se puede generalizar esta idea a un quema de *paridad par bidimencional*, donde en caso de darse un error de bit (en solo un bit) se garantiza no solo que se puede detectar sino tambien reparar. 
La capacidad que tiene un receptor para detectar y corregir error de la llama como *FEC*. 
Las tecnicas FEC son muy utilices ya que reducen el numero de transaccones, y sobre todo que al poder corregir los errores en tiempo real durante la trasmicion, se ahorra el retraso de propagacion del NAK del receptor informandole al emisor que haga una retrasmicion (capa de transporte). 

## Suma de comprobacion
La suma de comprobacion consiste en dividir los `d` bit a enviar en palabras de largo `k`, y utilizar el resultado de la suma como bit de deteccion de errores. 
La *suma de comprobacion de internet* utiliza esta idea, pero con k=16 bits. Luego todas estas palabra se suman y se envia por la red el complemento a1 de la suma. Luego el receptor suma todo (inclusie los bit de comprobacion) y le tiene que dar todo 1 el resultado. TCP y UDP usan este mecanismo, y cubren todo el segmento (cabecera incluida), Ip tambien lo usa, pero solo verifica el la cabecera. Como la capa de enlase es implementada por hardware, se pueden utilizar mecanismos mas complejos y seguros, como es CRC. Los mecanims de deteccion y correcion por software tiene que ser mas ligeros.  

## Comprobacion de redundancia ciclica (CRC)
No me voy a poner con detalles con eso, para eso mirar el libro que esta claro y es corto. 

La idea basica es que uno quiere enviar `d` bits con un texto `D`. Para ello acuerda con el receptor un genedor `G` de `r+1` bits. 
La idea es enviar un numero de la forma D + (concatenado) R tal que sea divisible por G. El problema claramente es como se calcula R. 
No se usan sumas ni restas con acarreo, por lo que hace que la suma y la resta funcionen cono XOR bit a bit. 

![[Pasted image 20221115181547.png]]

En ese caso nosotros queremos encontrer un `R` que cumpla que exite un `n` tal que:

$D.2^r \text{ } XOR\text{ } R = nG$
En otras palabras: 
$R = resto\text{ } \frac{D.2^r}{G}$ 

La IEEE ha definido estandare para genedores, se utiliza mucho en la capa de enlase el G de CRC-32 (osea 32 bit en G).

**Importante:**
Cada uno de estos generadores nos garantiza que los errores de `r` o menos bits seran detectados, incluso los de rafaga. y que todos los que tengan un numero impares de errores tambien seran detectados. 

