La funcion principal de un router es recibir las tramas y re-enviar las mismas a los puertos de salida correspondientes. 
El funcionamiento del switch debe ser *transparente* para los hosts y los routers. Por lo que cuando los nodos reciven/envian tramas, no tiene ni idea que habia uno o mas switches en el medio. 

Las interfaces de un switch de salida de un buffer puede recibir tramas mas rapido de las que las puede enviar por el switch, es por eso que se tiene *buffers* para almacenar estas tramas. 

