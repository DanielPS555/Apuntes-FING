El formato de los datagramas IPv4 son los siguientes: 

![[Pasted image 20221024212750.png]]

- ``Version``: (4 bits) Con eso podemos identifcar si estamos ante ipv4 o ipv6
- ``Longitud cabecera``: (4 bits) Lonigtud de la cabcera IP medica en bytes, el el campo de opciones no tiene nada, es de 20 bytes. 
- ``Tipo de servicio`` : Tambien conocidos como bits (TOS) identifican los distintos tipos de de datagramas IP. Por ejemplos lo que no corresponden a tiempo real y los que si. Tambien se usa para el *ECN* (Es el sistema congestion explicita que implementa TCP)
- `Longitud de dataGrama:` (16 bits), tiene la logitid en bytes del datagrama total. 
- `Identificador, indicador y desplazamiento de fragmentacion`: En la seccion de [[Fragmentacion IPV4]]
- `Tiempo de vida` (TTL): Es la cantidad de routers mas que podra transitar antes de eliminarse, cuando llega al router se vaja en una unidad, el router que lo degrade a 0 lo elimina. 
- `Protoclo capa superior`: Define el protocolo de capa superior (transporte) a la que se le pasara el datagrama. 
	**Importate**: 
	- Notar que esto hace el mismo efecto el numero de puerto en el proceso de desmultiplexacion en la capa de trasnprote. 
	- En TCP el valor es 6 y en UDP es 17

- `Suma de comprobacion en la cabecera`: Calcula de igual forma que UDP un checksum de *solo la cabecera TCP* . Cada router debe volver a realizar esta comprobacion y actualizar el checksum del datagrama, ya que el TTL cambia por enlase (osea cambia tambien la cabecera y por ende el checksum): Notar que esto no tiene nada que ver con la comprobacion TCP, es mas, nada nos dice que podamos sustituir uno checksum con otro, ya que no tienen porque estar en la misma pila de protocolos. 
- `Opciones`: Tiene tamaño variable, se envia la informacion extra por aqui. Esto afecta el tiempo de procesamiento en los routers, ya que la cantidad de informacion a procesar es variable. En ipv6 esto se saco. 
- `Ip origen y destino`: dirrecion de origen y destino. 
 