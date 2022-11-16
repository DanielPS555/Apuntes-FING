En esta capa nos ocuparemos de como se envian los paquetes entre enlases individuales. 

Hay dos tipos de canales.

- `Canal de difucion`: Este canal conecta a varios host. Se tiene que cordinar entre si para la utilizacion del medio. Para ello se utilizan *protoclos de acceso al medio*.
- `Canal punto a punto (PPP)`: Aqui solo se conectan dos dispositivos

Los datagramas que llegan de la capa de red son enviados por estos enlases a traves de una *trama de capa de enlase*.

Aunque sea sierto que el servicio basico de la capa de enlase dea mover tramas de un nodo a otro, hay otros ciertos servicios que esta puede oferecer:
- `Entramado`: El datagrama de capa de enlase en encapsula dentro de una trama, donde ademas se incluyen una serie de datos de cabecera. 
- `Aceso a enlase`: El protoclo puede traer consigo un *protoclo de acceso a medios* (MAC) el cual le indica a los host como trasmitir sus mensajes a lo largo del canal. Es muy simple cuando es un canal punto a punto y solo uno de los dos emite. Mas interesante cuando hay multiples nodos. 
- `Entrega fiable`: Algunos protoclos de capa de enlase implementan sistemas de entrega fiable de datos. Sobre todo aquellos que utilizan un enlase con alta tasa de fallos, ej inalambricas. 
- `Deteccion y correcion de errores`:  Algunas implementaciones manejan detecion de errores (generalmente por hardware) y otros ademas tiene sistemas de correcion de errores. 

## ¿Donde se implementa la capa de enlase?
Depende. En un router en la targeta de linea de los puertos de entrada y salida. 
En los sistemas terminales por lo general reside en las *targetas de interface de red*. El corrazon de las mismas por lo general es un chip que implementa los protocolos de la capa de enlase espesifica para el tipo de enlase para la que fue diseñada. 
![[Pasted image 20221107032635.png]]

De todas formas no toda la capa de enlase de implementa por hardware, las funcionalidades mas complejas de ejecutan por software en el CPU. Por ejemplo del lado del emisor se encarga por software del Ensamblado de la informacion de direccionamieto de capa de enlase [Aun no se que es eso] y la activacion del hardware. Y del lado del receptor, a nivel de software se manejan cosas como responder interupciones, gestionar condiciones de errores, pasar datagramas a la capa de red.