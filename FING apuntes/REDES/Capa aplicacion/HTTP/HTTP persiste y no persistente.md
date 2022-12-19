# HTTP Persistente y no persistente

HTTP en su version 1.0 no soportaba *conexiones persistentes*, por lo que todas ellas eran *conexciones no persistentes*. 

## Conexciones no persistentes
Este este tipo de conexcion, por cada peticion HTTP se crea una nueva conexcion con el servidor, por lo que cada vez que se quiera consultar algo se tiene que hacer el proceso de threehandshake TCP. Luego de hacer la peticion se cierra la conexcion. Se pueden realizar *conexciones TCP en paralelo*, por lo general los nevageadores permiten entre 5 a 10 de estas. 

Como se tiene que crear una conexcion por cada objeto solicitado, ademas tenemos un retraso de `2 RTT + tiempo de tranferencia` por cada uno de estos objetos. 

No se requeria de el header Content-length ya que en el stream TCP solo podria ir una peticion HTTP. Por lo que no importaba del todo saber cuando habia termiado el objeto, eso lo sabia cuando cerraba la conexcion. 

## Conexciones persistentes
En este tipo de conexcion se introdujo para HTTP en la version 1.1. En esta , luego de hacer la peticion HTTP, se deja activa la conexcion. Por lo general se cierra luego de un tiempo. 
La forma para saber que se esta utilizado es que en el header Conection se pone 'keep-alive'.
Esto significa que puedo hacer varias consultas HTTP sin tenes que volver a establecer la conexcion nuevamente,
En HTTP 1.1 soporta el *procesamiento en cadena* , por lo que el cliente puede hacer varias consultas sin tenes que esperar la respuesta. El servidor va a contestar estas peticiones en el orden en que se hicieron. 





