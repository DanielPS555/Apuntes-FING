Alguna terminologia: 
- `Host`: Son los *sistemas terminales* donde se ejecuta el proceso que quiere emitir o recivir una informacion 
- `Conmutador de paquetes`: Son utilizados los sistema que viven en el nucleo de la red, reciven paquetes por un puerto y los envian por otro. Los mas comunes con *Routers* y los *Switches*
- `Ruta`: Conjunto de conmutadores que recorre un paquete para ir del host emisor al host receptor


## Introducion
- Se puede ver a internet desde el punto de vista de las aplicaciones		
> Internet es una infraestructura que proporciona servicios a las aplicaciones
- Las aplicaciones que utilizan requieren de multiples terminales para funcionar se las conoce como *Aplicaciones Distribuidas*
-  Los programas se comunican con la red (Espesificamente con la capa de transporte) via *sockets*.  La cual no es mas que una interface. Una API desde el punto de vista de las aplicaciones, ya que ellas ven a internet como una gran librearia las cuales los sockets exponen. 
- `Protocolo` : 
	La definicio es:
	> Un protocolo define el formato y el orden de los mensajes intercambiados entre dos o mas entidades que se comunican, asi como las acciones tomadas al producirse la transmicion y/o recepcion de un mensaje y otro suceso.
	
	Los protoclos no privativos (*estandares de internet*) son documentados en los documentos conocidos como *rfc* 
	

Internet es muy basto para verlo a modo general. Por lo que se pueden analizar dos grandes partes: [[Frontera de la red]] y el [[Nucelo de la red]]





## ISP
Los ISP son los proveedores de servicio de Internet. Hay ISP recidenciales, universitarios, corporativos entre muchos otros. Por lo general hay 3 niveles de ISP, los de nivel 1 se comunican todos entre si. Luego lo de menor nivel utilizan a los de mayor nivel. 