# Frontera de la red
La frontera de la red es donde se albergan los sistemas terminales. Dependiendo de la arquitectura del sistema, estos host se puede diferenciar en *clientes* y *servidores*.

## Redes de acceso 
Las redes de acceso son lo que conecta fisicamente los sistemas terminales son su primer conmutador de paquetes (por lo general un router). 

### DSL y Acceso por cable
Bajo esta metodologia se utiliza la propia linea telefonica como medio de internet. En esos casos los proveedores de telefono son tambien son ISP.

La PC se conecta a un model DSL el cual convierte la informacion del PC a todos de alta frcuencia. Luego un circuito separador se encarga de convinar la señal del telefono con la del model, o redirigir una al model y otra al telefono. Los rangos de frecuencia son:
- Linea de telefono 0 - 4KHz
- Carga de datos 4 - 50KHz
- Descarga de datos -50KHz a 1MHz

![[Pasted image 20221002023828.png]]

Esos todos viajan hasta la central de telefomo, donde un DSLAM hace el trabajo inverso. Separa las los canales de frecuencia y dijitaliza los datos que eran del sistema terminal, donde los ingresa a internet. 


Por otro lado, el *Acceso por cable* utiliza la infraestructura del cable en vez del telefono. En estos sistemas se utiliza cablez coxial para llegar desde el nodo mas cercano hasta cada vivienda. Y entre los nodos y las centrales se usan fibra. A diferencia de un DSLAM se utilza un *CMTS*. Lo que hay que tener cuidado es que en esta ultima, el canal es un contenido de descarga comun, por lo que si un paquete de informacion se descarga, le llega a todos los usuarios. Ademas el hecho que varios host descargen a la vez afecta la velocidad de todos los Host de la red de ese nodo. 

![[Pasted image 20221002025413.png]]


### FTTH
Por lo general las fibras que se emiten de la central son compartidas por varias viviendas. Donde la divicion es muy proxima a la ubicacion de las mismas. 

Por lo general la arquitectura es que cada host se conecta a la fibra mediante un *ONT* , luego con fibra cada ONT viaja a un distribuidor que le envia tambien por fibra a la central los paquetes a un *OLT* 

Hay dos tecnologias de redes de fibra optima. 
- `Redes optimas pasivas (PON)`: En esta tecnologia, cuando el OLT envia un mensaje al distribuidor este se la envia a cada host que esta conectado a el. 
- `Redes optimas activas (AON)`: No habia informacion en este cap
![[Pasted image 20221002030356.png]]

### LAN (domestica o empresarial)
Es una red privada domestica o empresarial, en la cual los host se pueden conectar a un router (o switch) por cable de cobre o a un access point via wifi. En esta red los host se pueden hablar directamente entre si sin pasar por la boca de salida del router. Hoy tambien en dia son comunes en los hogares.

### 3g y LTE

## Medios fisicos
Los medios fisicos se pueden dividir en dos categorias: 
- `Medios guiados` : Las ondas de informacion van canalizadas por un medio fisico.
- `Medios no guiados`: Las ondas no van concentradas por ningun medio fisico. Viajan por el espacio

Algunos medios son los siguientes: 
- `Cable de cobre de par trenzado` : Tambien conocido como *UTP*, se utiliza para redes dentro de una LAN
- `Cable coaxial` : Se utiliza generalmente como medio compartido, es decir: multiples terminales conectados al mismo enlase y todos reciviendo la informacion de los otros.
- `Fibra optima`: Es un enlase muy veloz, muy poco sensible a interferencias electro magneticas y atenuacion muy baja.
- `Canales de radio terrestres`: Son los clasicos canales de radios que todos conocemos. Lo que si se pueden dividir en 3 grupos: 
	- Operan a distancia muy corta (2 metros por ej)
	- Operan en areas locales 
	- Operan en areas extensas
- `Canales de radio via satelite`: Los satelites reciven una señal en una frcuencia dada, la replican y la emiten en otra frecuencia. Hay dos tipos dependiendo de donde este el satelite:
	- Salite geoestacionario: Se encuentra en la orbita geoestacionaria, por lo que rota a la misa velocidad que la tierra. La orbita esta a 36000km de la superfice terrestre
	- Satelite de orbita baja terrestre: estan mas cerca de la tierra, por lo que tiene menos retardo en replicar el mensaje, pero no se mantiene en un mismo lugar en la tierra, por lo que para asegurar covertura en un area determinada se requiere de varios de estos satelites. 
