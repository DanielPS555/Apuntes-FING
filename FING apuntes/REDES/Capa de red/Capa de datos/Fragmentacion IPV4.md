La capa de enlase tiene lo que se conoce como *unidad maxima de trasmicion* (MTU), el cual nos limita el tamaño maximo del datagrama que podamos enviar de enlase a enlase. Esto no seria un problema ya que podriamos acotar el datagrama a ese tamaño. Pero verdadero problema es que el MTU cambia por enlase, osea puede cambia durante la ruta. 

La solucion consiste en que cuando nos enfrentamos a un MTU mas pequeño que el datagrama que tenemos actualmente, lo *fragmentamos*. Estos fragmentos son rensablados en el reseptor. 

Para la fragmentacion utilizamos una serie de cabezales que son: *indentificador*, *indicadores* y *desplazamiento de fragmentacion*. 

Cuando se crea un *datagrama* se le asigna un numero de identificacion. A la hora que un router fragmenta , se copia su ip de origen, destino, identificador. 

Luego para rensamblar se utiliza el bit *indicador*, si esta pueso en 0 indica que ese es el ultimo fragmento, sino (esta en 1) indica que ese no es el ultimo framento. Tambien se usa el campo *desplazamiento de fragmentacion* para numerar los fragmetos con el fin de ordearlos para entregarlos, o asegurarse que todos le llegaron


Es importante mirar el siguiente ejemplo a detalle, sobre todo notar que el offset no indica el byte donde comienza el fragmento, sino el octeto donde comienza 
![[Pasted image 20221118173816.png]]

