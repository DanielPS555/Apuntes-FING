# Correo eletronico 

Este tipo de aplicacion ha existido desde el inicio de internet. 

Los principales actores son:
- *Agentes de usuario* : los las aplicaciones que usa el usuario para acceder a su correo
- *Servidores de correo*: Los servidores donde se aloja el buson de correo de los usuarios
- *Protocolo de tranferencia simple (SMTP)* : Es el protoclo que se utiliza para hacer la tranferencia de los correos entre los agentes a los servidores y entre los servidores en si. 

Cada usuario de correo tiene su buson de correo en un servidor de correo, en el se almacenan los correos que ha enviado y los que ha resivido.

## Forma de envio (SIN POP3, IMAP o HTTP)
Cuando un usuario quiere enviar un correo, lo hace desde su *agente de usuario* desde ahi via *SMTP* envia un mensaje a su servidor de correo, indicando a quien le quiere enviar ese correo. Si es un buzon que se encuentra dentro del mismo servidor, hace el movimiento. Si se encuentra en otro servidor se intenta enviar por SMTP. Si el envio no se pudo dar, se lo ingresa a la en la *cola de mensajes* y se vuelve a intentar cada 30 min, si luego de un numero de intentos no se logra enviar, se elimina de la cola y se le notifica al usuario.  Cuando llega al servidor destino, el mismo es situado en el buzon del usuario correspondiente. 

## SMTP
- Definido en el RFC 5231 
- Usa TCP en el puerto 25
- Todos los mensajes van codificados en ASCII
- 



