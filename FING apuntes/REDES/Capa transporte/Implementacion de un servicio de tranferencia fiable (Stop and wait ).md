# Implementacion de un servicio de tranferencia fiable (Stop and wait )

La idea de esta seccion es ir contruyendo un *servicio de traferencia fiable* (como por ejemplo TCP) en la *capa de transporte*, *sobre un servicio de traferencia no fiable de la capa de red*, como puede ser el caso de IP.

Para ello se iran biendo diferentes *rdt* (reliable data tranfert) que vayan sortado diferentes desafios. 

**Importante**: 
- Se asume que todos los paquetes llegan en el mismo orden en que fueron enviados
- Todos estos protoclos son de tipo *stop and wait* 

## rdt 1.0  (canal completamente fiable)

![[Pasted image 20221005113727.png]]

## rdt 2.0 (canal que puede corromper mensajes en la ida)
Ahora tenemos que de alguna forma notificar el emisor que el paquete llego correctamente o incorrectamente. 

Los protoclos de tranferencia fiable basados en re-trasmiciones se los conoce como *ARQ*, los protoclos de tipo ARQ tiene 3 capacidades que debe cumplir:
1. *Deteccion de errores* : el receptor debe ser capaz de darse cuenta que el paquete llego corrputo
2. *Realimentacion del receptor*: Es que el receptor le envie explicitamente informacion de realimentacion al emisor.  Puede ser respuestas de *reconocmiento positivo* o de *reconocimiento negativo*
3. *Retrasmicion*: un paquete que haya llegado corrputo al receptor, debe ser retrasmitido por el emisor. 

Se puede hacer utilizando paquete *ASK* y *NAK* para notificar que el paquete llego correctamente o mal respectivamente. 
![[Pasted image 20221005123746.png]]

Notar que eso NO tiene en cuenta que tambien se puede corromper un paquete de reconocimiento. 

## rtd 2.1 (canal que puede corromper mensajes de ida y vuelta, usando ASK y NAK)

Para poder prever que se rompa el mensaje de confirmacion, se puede añadir un numero de secuencia a los mensajes que envia el emisor. En este caso con un numero de secuencia que haya de 0 a 1 sera suficiente. 

![[Pasted image 20221005134144.png]]


## rtd 2.2 (canal que puede corromper mensajes de ida y vuelta, usando solo ASK)
Podemos tambien utilizar la idea del numero de secuencia en el mismo ASK, de esta forma podemos evitar utilizar el reconocimiento de tipo NAK. De esta forma, el emisor espera un ASK con la misma secuencia que el envio.  

![[Pasted image 20221005134850.png]]

## rtd 3.0 (canal que puede corromper mensajes o perderlos)
Ahora tenemos la posibilidad de que el paquete nunca llege al receptor, o que el mensaje de confirmacion del receptor nunca llege al emisor. Es por eso que ahora el emisor pone un timer, en caso que el emisor no tenga una respuesta del receptor en un tiempo, vuelve a enviar el paquete. Esto puede producir mensajes de confirmacion duplicados.

La foto adjunta es solo del emisor que es quien cambia, el receptor es identico al rtd 2.2

![[Pasted image 20221005140714.png]]
