# UDP

UDP es uno de los dos principales protoclos que oferece la capa de transprote. 

De los servicios que la capa de transporte oferece, *la entrega de datos proceso a proceso* y *la comprobacion de errores* son los unicos que UDP oferece.


## Envio de un mensaje UDP
UDP toma el mensaje de la capa de aplicaciones, si el mensaje no supera el maximo, se lo empaqueta en un segmento, donde se setean los 4 campos de la cabecera. 

Luego se le pasa directamente a la capa de red para que se encarge del envio. Notar que no hubo ninguna etapa de negociacion con el receptor, es por eso que se trata de un *protoclo sin 
conexcion*. 

## Ventajas de UDP frente a TCP
- *Mejor control a nivel de aplicacion sobre que datos se enviaron y cuando*: Tengamos en consideracion que todos los datos se envian en un solo segmento, por lo que podemos saber cuales datos ya se enviaron y cuales no. Ademas como UDP no tiene mecanismo de control de congestion, el segmento se envia apenas llega de la capa de aplicacion. Esto puede ser veneficioso de las *aplicaciones de tiempo real*, donde esperar a que la red deje de estar congestionada puede que no sea una opcion. 
- *Sin establecimiento de conexcion*: Como ya dijimos UDP es un protocolo sin conexcion, por lo que no hay retrasos por los mensajes de negociacion. 
- *Sin informacion del estado de la conexcion*: TCP es un protoclo con conexcion, por lo que para cada una de estas conexciones debe mantener diferentes recursos. Como pueden ser buffer de envio y recepcion, numero de secuencia y de reconocimiento, parametros para el control de congestion, etc. UDP se ahorra todo eso ya que no tiene estado, por lo que si una aplicacion se servidor funciona con UDP, es posible que esta soporte mas clientes. 
- *Menor tamaño de cabecera*: La cabercera UDP mide unos 8 bytes, mientras que la TCP como minimo unos 20 bytes. 

El hecho que UDP no tenga control de contingencia podria ser visto como algo positivo por las aplicaciones que lo utilizan, ya que por ejemplo los sistemas de tiempo real (como el telefono), no pueden esperar a que la congestion de la red baje para operar. 
Pero al mismo tiempo se lo puede ver como algo malo, ya que cuando hay una alta congestion en la red la tasa de perdida puede ser muy elevada, e incluso los propios segmentos UDP aumentan incluso mas la congestion, haciendole un mal tremendo a la red en general. 

## Estructura de los segmentos UDP
La estructura del segmento UDP es la siguiente: 
![[Pasted image 20221005012802.png]]

- *Nº puerto origen* = puerto del socket que emite el mensaje UDP
- *Nº puerto destino* = puerto del socket que deberia recibir el mensaje UDP
- *Longitud* = Longitud total del segmento expresado en bytes 
- *Suma de comprobacion* = Es el complemento a 1 de la suma de todas las palabras de 16 bit, donde ademas es desbordamiento durante la operacion (un bit de carry al final de la suma) se suma al bit menos significativo.