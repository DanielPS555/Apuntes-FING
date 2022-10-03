## Arquitectura
En la capa de red es donde viven las aplicaciones, y por ende sus protoclos. 
Lo primero que uno podria decir de la capa de aplicaciones es los tipos de arquitecturas que se pueden encontrar. 
- `Arquitectura cliente - servidor`:  En esta arquitectura los host asumen papeles determinados, donde encontramos los *roles* de *servidor* y los de *cliente*. El servidor centralisa las peticiones de los clientes, y es el que responde a pedidos de los clientes. 
	`Caracteriticas de un servidor:`
	- Siempre activo 
	- Tiene una dirrecion fija y conocida por los clientes. 
	- Debido a la demanda suelen utilizarse *centros de datos*
	
	`Caracteristicas de un cliente`:
	- Es intermitente (no estan siempre prendidos)
	- Aparecen a demanda (cuando el cliente lo presisa)
	- Su dirrecion no es fija
   La gran Ventaja de las aplicaciones clientes- servidor es que al ser centralizadas se puede controlar mejor la seguridad y el rendimiento. Aunque es complicado la auto-escalabilidad.    

- `Arquitectura peer to peer (P2P)`: En esta arquitectura la dependencia con los servidores es poca o casi nula, lo importante notar aqui es que *los roles no son fijos*. Los host se conectan entre si dirrectamente. La gran ventaja de este tipo de conexciones es la *auto-escalabilidad*

Las aplicaciones de host diferentes se comunican intercambiando *mensajes*. En una comunicacion se determina un *cliente* y un *servidor*, donde de la pareja de procesos que se estan comunicando, el cliente es que el comenzo la comunicacion, mientras que el servidor es el que esta esperando se contactado por el cliente. Notar que eso **no depende de la arquitectura** es algo propio de la comunicacion entre dos procesos. 

## Socket
Los procesos acceden a internet via *socket*. El proceso va a enviar estos mensaje y recivirlos por un socket. Este ultimo no es mas que una *API* (Aplication programming interface), ya que el socket para la aplicacion no es mas que una interface que expone una libreria que es internet. La aplicacion puede intervenir muy poco en como se envia el mensaje (por ejemplo puede elegir si se va a enviar por UDP o TCP), pero no mucho mas. 
En otras palabras, el socket se encuentra en la frontera entre la capa de aplicacion y la capa de transporte. 
Los sockets tiene asignado dentro del host donde se ejecutan un *numero de puerto* asi cuando se recive un mensaje, se save a que socket hay que enviarlo. 

## Algunas otras clasificaciones 
Los *protocolos de datos fiable* son aquellos que garantiza la entrega datos entre los dos host, por ejemplo TCP. 
Las aplicaciones que aceptan trabajar con protoclos no fiables son *aplicaciones tolerantes a perdidas*, un buen ejemplo de esto son aplicaciones multimedia.

Tambien hay que tener en cuenta que son *aplicaciones sensibles al ancho de banda*, que como su nombre lo dice requieren de determiado ancho de banda para poder funcionar, mientras que las *aplicaciones elasticas* son aquellas que hacen uso de la tasa de tranferencia disponible, por ejemplo las aplicaciones de correo electronico. 

## Seguridad
Ni TCP ni UDP brindan cifrado a los mensajes que envian. Es por eso que se desarrolo una mejora para TCP llamada *SSL*, la misma se utiliza en capa de aplicacion, y la misma provee de su propia API de sockets. Donde se cifran los datos antes de enviarlos, de forma que el receptor puede luego desencriptarlos. 
