# Correo eletronico 

Este tipo de aplicacion ha existido desde el inicio de internet. 

Los principales actores son:
- *Agentes de usuario* : los las aplicaciones que usa el usuario para acceder a su correo
- *Servidores de correo*: Los servidores donde se aloja el buson de correo de los usuarios
- *Protocolo de tranferencia simple (SMTP)* : Es el protoclo que se utiliza para hacer la tranferencia de los correos entre los agentes a los servidores y entre los servidores en si. 

Cada usuario de correo tiene su buson de correo en un servidor de correo, en el se almacenan los correos que ha enviado y los que ha resivido.

## Forma de envio
Cuando un usuario quiere enviar un correo, lo hace desde su *agente de usuario* desde ahi via *SMTP* envia un mensaje a su servidor de correo, indicando a quien le quiere enviar ese correo. Si es un buzon que se encuentra dentro del mismo servidor, hace el movimiento. Si se encuentra en otro servidor se intenta enviar por SMTP a dicho servidor, pero primero se lo coloca en una *cola de mensajes*. Si el envio no se pudo dar, se mantiene en la  cola de mensajes y se vuelve a intentar cada 30 min, si luego de un numero de intentos no se logra enviar, se elimina de la cola y se le notifica al usuario.  Cuando llega al servidor destino, el mismo es situado en el buzon del usuario correspondiente. 
Es importante que el cliente envie el correo su servidor de correo para que este lo envie al servidor de correo del receptor, en vez de el enviarlo directamente. Ya que sino no se podria re intentar.
Por ultimo, cuando el usuario receptor asi lo desee, ingresara a su agente de usuario de correo, el cual descargara los correos de su servidor de correos utilizando un protoclo como *IMAP* o *POP3*. O sino se conectara con un *Servidor web* para conseguir un agente de correo web, el cual trabajara con copias de los mensajes. Considerar que el servidor web esta en el mismo servidor que el servidor de correo, o sino consigue los correos tambien con POP3 o IMAP

## SMTP
- Definido en el RFC 5231 
- Usa TCP en el puerto 25 (inseguro) o 465 (seguro)
- Todos los mensajes van codificados en ASCII de 7 bits. Esta codificacion compejisa las cosas cuando hay que codificar archivos multimedia
- No se utilizan servidores intermedios. Si los dos servidores de correo estan del otro lado del mundo, entonces el mensaje se envia directo.
- SMTP tiene una *etapa de negociacion a nivel de aplicacion*, en la que el cliente SMTP espesifica  el *correo emisor y receptor*. Luego el cliente envia el mensaje. 
- SMTP tiene una serie de comandos:
	- *HELO* IDENTIFICACION . Luego que el servidor SMTP se haya identificado con el codigo 200, enviamos el comando HELO identificado ahora al cliente SMTP con el servidor. Si todo sale bien nos debuelve codigo 250
	- *MAIL FROM* < CORREO EMISOR >  :  Definimos el correo emisor. Si todo sale bien nos debuelve 250.
	- *RCTP TO* < CORREO RECEPTOR > : Definimos el correo receptor. Si todo sale bien nos devuelve 250. 
	- *DATA*: Luego de ingresado nos devuelve el codigo 354 diciendo que ya podemos escribirm a continuacion el cliente escrive el mensaje linea a linea, cuando se termina se deja un renglon con solo un '.', El caso de que el mensaje sea aceptado nos debueve 250, 
	- *QUIT*. En caso que no queramos enviar otro mensaje (que comenzariamos nuevamente con el MAIL FROM), se envia el comando QUIT, el cual nos devuelve el codigo 221 
![[Pasted image 20221004112638.png]]
- El formato del *mensaje SMTP* tambien esta definido. Luego de haber ingresado el comando DATA, va el mensaje, que tiene dos partes, la primera son las *Lineas de cabecera* y luego el *Cuerpo del mensaje*.
  Las lineas de cabecera son las siguientes (en orden)
  1. *From* : emisor del correo
  2. *To*: receptor del correo
  3. *Subject*: Asunto del correo

## Diferencia entre SMTP y HTTP
Es cierto que ambos protoclos se emplean para tranferior archivos de un host a otro, pero hay cierras diferencias a remarcar. 
- HTTP es un *Protocolo PULL* utilizado para la extraxion de datos, mientras que SMTP es un *Protocolo PUSH* utilizado para insercion de datos en el servidor desde un cliente. 
- SMTP funciona en ASCII de 7 bit, mientras que HTTP no tiene no tiene limitado su formato. 
- HTTP encapsula cada objeto y para cada uno de ellos se requiere de una peticion distinta, en SMTP todos los objetos del correo se envian en un solo mensaje. 

## Protocolos de acceso para correo electronicos
Como el protoclo SMTP es un protoclo PUSH, no le sirve al usuario receptor para conseguir su correo desde su agente de usuario. Es por eso que se añaden algunos nuevos protocolos: *POP3* y *IMAP*. 

## POP3
   
POP3 es uno de los protocolos que utilizan los agentes de usuario para obtener correos del servidor de correos. 
Utiliza el puerto es el 110(inseguro) y 995 (seguro) y el RFC 1939. 

Es un protocolo muy simple que consiste en 3 etapas:
- *Autorizacion*: El agente envia el nombre de usuario y la contraseña para autentificarlos.
- *Transaccion:*  Aqui se pueden listar los correos, descargar los correos, marcar para borrarlos, y eliminar la marca para borrarlos. Tambien se pueden obtener datos estadisticos. 
- *Actualizacion:* Al ingresar el comando *quit*, se impactan los cambios en el servidor. Por ejemplo se eliminan los correos marcados. 


### Comandos
- *user*: Es el primero comando que se ingresa, identifica al usuario
- *pass*: Es el segundo comando que se ingresa, es la contraseña del usuario
- *list*: Lista los correos por un contador (que los identifica) y por el tamaño de cada uno.
- *retr*: Se utiliza para descargar el correo identificado por su identificador (dado en el list)
- *dele*: Se utiliza para marcar que ese correo debe ser eliminado, se lo identifica al correo con su identificador (dado en el list)
- *quit*: Con ese comando el servidor entra en estado de actualizacion, impactando los datos necesarios.

Todos los comandos tiene dos posibles respuestas *+OK* , *-ERR*. 

**Importante:** POP3 no tiene estado entre secciones de POP3, si tiene un estado durante la seccion (que recuerda a quien debe borrar y a quienes no)

## IMAP
IMAP es una actualizacion del POP3, con mas funcionalidades. 
Utiliza el puerto 143 (inseguro) y el 993 (seguro) y esta definido en el RFC 3501.

IMAP permite crear carpetas remota (con su jerarquia), mover correos a estas carpetas, obtener partes espesificas del mensaje de un correo, entre otras funcionalidades. 

**Importante**: IMAP si tiene estado entre las secciones, ya que por ejemplo la jerarquia entre las carpetas, sus nombres y que correos tiene asignados se mantiene entre distintas secciones. 

## Correo electronico web
Ahora los usuarios pueden acceder a sus correos mediante los navegadores web, via solicitar un *user agent web* via HTTP a un servidor web. Ese servidor web se comunica con el servidor de correo via POP3 o IMAP para obtener los correos a mostrar y luego presentarlos el un documento web que se envia con HTTP al navegador. 





