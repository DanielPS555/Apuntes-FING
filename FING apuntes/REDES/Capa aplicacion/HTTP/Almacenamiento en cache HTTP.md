# Almacenamiento en cache HTTP

Una *Cache HTTP*, o tambien conocido como *servidor proxy* es una entidad intermediaria entre el cliente y el servidor. Se configuran los navegadores para que en vez de enviar la request al servidor, la envien al proxy. 

La idea es que las proxys guarden los objetos pedidos por los clientes, para que si otro cliente pide lo mismo, el proxy pueda contestarle rapidamente. 

Por lo general son los ISP de universidades, empresariales quienes colocan los servidores proxy, aunque hoy en dia son generalmente los *CDN* quienes instalan estas proxy en puntos estrategicos.

## Funcionamiento 
1. El navegador crea una conexcion TCP con el servidor proxy y envia la HTTP request
2. La cache comprueba sin tiene o no una copia objeto solicitado. (No estoy seguro de este paso con el *get condicional*)
3. Si no la tiene, utilizando la linea de cabecera *Host*, crea una conexcion TCP ahora con el ese servidor, y envia la HTTP request
4. Cuando recive la respuesta, guarda una copia de la misma y le envia otra al cliente que en primer lugar se consulto a la proxy. 

## Get condicional
Un problema que tenemos con el modelo actual del proxy es que no tenemos forma de saber si el elemento que esta en la cache sigue siendo o no invalido. Es por eso que se creo el concepto de *get condicional*. 
La idea es la siguiente: Por lo general, cuando el servidor le contesta al proxy con un archivo, se tiene la linea de cabecera *Last-Modified* la cual dice la ultima fecha en la que se modifico el recurso. Luego, cada vez que el proxy recive una consulta, **en vez de contestar con su copia, envia la peticion get al servidor**, pero con la linea de cabecera *if-modified-since* con valor de la ultima fecha del modificacion que el servidor proxy conosca. El servidor recibira la HTTP request, pero solo contestara con el objeto si el objeto fue modificado luego de la fecha enviada por la cabecera if-modified-since. En caso de que la HTTP responce llege sin objeto al proxy, este contesta con su copia, sino actualiza su copia, la fecha de modificacion y devuelve dicha copia. 

## Motivos para el uso del Servidor Proxy
Hay principalmente dos motivos para implementar un Servidor proxy. 
1. Reducir el tiempo de respuesta de la solicitud de un cliente. Sobretodo si el ancho de banda cuello de botella entre el cliente - servidor es sustancialmente menor que el proxy - servidor.
2. Reducir el trafico en el enlase de acceso a internet de la institucion. Evitando que la insitucion deba mejorar el ancho de banda que su ISP le provee.