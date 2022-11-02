## Como funciona en la vida real
En la vida real no sucede que todos los routers ejecutan el mismo algoritmo de enrutamiento. Ya que hay dos problemas con eso:
- *Escala*
- *Autonomia administrativa*: Por lo general los ISP manejan sus redes como les pinta. 

Por lo que se crean creando *sistemas autonomos* (AS) donde cada AS esta conformado por una red de routers y se encuentran acargo del mismo control administrativo. 
Algunos ISP se manejan con un solo AS, mientras que otros utilizan multiples AS.
Todos los AS se identifican con un solo *identificador de sistema autonomo*, el cual es un identificador global, brindado por la ICANN.

Dentro del AS se ejecuta el mismo algoritmo de enrutamiento. El protocolo de enrutamiento utilizado dentro del AS se lo conoce como *protocolo de enrutamiento interno del sistema autonomo*

## OSPF

OSPF es un protoclo disponible publicamente. Utiliza la tecnica de *indundacion de informacion de los enlase* y para el calculo de la ruta *el algoritmo Dijkstra* . Con la informacion de los enlases, el algoritmo construye un mapa completo de la topolia de la red. 
Luego es responsabilidad del administrador estableser los costes de los enlases. Luego OSPF calculara en cada router la ruta mas corta en base a los algoritmos.  

Con OSPF se envian mensajes con el estado de los enlases a todos los routers del AS, no solo los vecinos. Los *anuncios OSPF* se envian en *mensajes OSPF* ,el cual trabaja directo sobre IP, por lo que tiene que implementar por si solo todo lo que presise de capa de transporte, por ejemplo la tranferencia fiable, el *numero de capa superior* de OSPF es 89. 
Los cambios se envian cada vez que un enlase se activa/inactiva, se cambia un costo o cada 30 minutos. 
Tambien los propios routers puede comprobar si un router sigue activo con un mensaje HELLO, o tambien puede obtener la proioa base de datos de un router vecino. 

### Algunas ventajas de OSPF
- *Seguridad*: Se puede agregar autentificacion a los mensajes OSPF. Por ejemplo autentificacion simple o por MD5. 
- *Utilizacion de varias routas de multiples coste*: Si hay varias routas de igual coste, puede elegir utilizar varias de esta, no tiene porque ser siempre la misma.
- *Soporte integrado para unidifucion y multidifucion*: MOSPF tiene las extenciones necesarias para permitir el enrutamiento multidifucion. 
- *Soporte de jerarquias dentro de un mismo AS*: OSPF permite definir *areas*, esas areas tiene routers internos y routers de frontera. Los routers de frontera se comunican interceptan con el *area troncal* (solo hay una de estas). Todos los paquetes que van de un area a otra area se envian a un router de frontera de su area, pasan a la troncal y luego se enrutan a la frontera dentro del area destino, luego se redirige a destino. 