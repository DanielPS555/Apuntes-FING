Como ya se menciono, cada AS utiliza el protoclo de enrutamiento que quiera. Pero ¿como se enrutan los paquetes que tiene que pasar por distintos AS?
Es por eso que los *AS se tiene que cordinar y utilizar el mismo algoritmo de enrutamiento entre ellos*. En particular todos los AS estan cordinado en el uso de *BGP* como protoclo de enrutamiento entre sistemas autonomos. 

BPG es un protoclo *decentralizado* y *asincrono* el cual esta en linea con el *vector de distancia*. Es uno de los protoclos mas importantes de internet, es completo y dificil [Para variar no?]


## Papel de BGP
BGP justamente se va a encargar de esos paquetes los cuales los routers dentro de AS no saben como routear. 

BGP no se enruta hacia una dirrecion en particular, sino hacia *prefijos CIDR* , donde cada prefijo representa una subred o un conjunto de subredes. 

### Mecanimos que proporciona BGP a los routers
- *Obtener de los AS vecinos informacion acerca de la alcanzabilidad de los prefijos*: Permite que cada red se pueda anunciar al resto de las redes. De esta forma se garantiza que ninguna red queda asilada del mundo. 
- *Determinar las "mejores" rutas hacia los distintos prefijos* Se determina localmente la mejor ruta basandose en la informacion disponible de la alcanzabilidad y de las politicas existentes. 

## Anuncion de informacion de rutas BGP
Cada AS tiene dos tipos de routers:
- *Router de pasarela*: Se encuentra en la frontera de la red. Esta conectado al menos a uno de otros routers de otro AS.
- *Router interno*: Solo se conecta con host y routers del AS. 
Los routers intercambian mensajes BGP por medio de conexciones TCP semi-permanentes en el puerto 179

Se le llama *conexcion BGP* a la conexcion TCP antes dicha entre dos routers. 
Si la conexcion es entre dos routers de dos AS diferentes, entonces se le llama *BGP externa* (eBGP) y si es entre dos routers del mismo AS se le llama *BGP interna* (iBGP). Notar que los enlases iBGP no son siempre fisicos, ya que es una conexcion TCP punta a punta entre dos routers. 

Una costa importante es que el mensaje de anuncion BGP se va pasando, y a medida que se le envia a una nueva AS, se le adjunta el AS de donde se le envia, formando asi una cadena de AS que se tiene que recorrer para llegar al AS que tiene el prefijo. Notar que solo se le agrega esta marca cuando el mensaje es eBGP, cuando es iBGP el router que recivio el eBGP se lo envia al resto del AS via iBGP.

## Determinacion de las mejores routas
Tambien puede pasar que para llegar al AS de un determinado prefixo, haya varias routas (formadas por AS) diferentes, es por ello que surge la necesidad de saber cual de estas rutas es la mejor.
Ante un anuncion BGP, no solamente se envia el prefixo, sino que tambien se envia la *ruta* , que es el prefijo + los atributos. 
Dos de esos atributos son:
- *AS-PATH* Esta variable tiene la lista de los AS por donde paso el anuncion previamente. 
- *NEXT-HOPE*: Es la dirrecion IP de la interfaces que conecta al ulimo AS del AS-PATH con el AS actual. La siguiente foto es clara
![[Pasted image 20221101015653.png]]
Notar que la dirrecion del NEXT-HOP no pertenece al AS actual, pero esta dirrectamente conectada a la AS.

### Enrutamiento de la patata caliente 
La idea con este enrutamiento es "sacar" paquete con el menor costo posible de la red del AS. En particular el router emisor utiliza el algoritmo de enrutamiento interno para determinar cual de los anuncion para el prefijo X tiene el NEXT-HOP de menor costo (para enviarle un mensaje desde ese router a el). Una vez que obtiene quien es el NEXT-HOP con el menor costo, obtiene de su tabla de re-envio la interfaces el router deberia re-enviar el paquete para llegar a esa interfaces, sea `I` esa interfaces. Entonces añade el registro `(x,I)` a su tabla de re-envio, donde `x` es el prefijo objetivo. 
![[Pasted image 20221101021112.png]]

### Algoritmo de seleccion de ruta
Ahora se utilizan varios pasos para elegir la ruta. Este algoritmo se aplica sobre todas las rutas que el router ha obtenido y autorizado. Los siguientes pasos funcionan a modo de filtro, y se aplican en el siguiente orden:
1. Elige las rutas con el *valor de preferencia mas alto*. El valor de preferencia se puede terminar por el propio router o por otro router del AS. Es 100% elegido por las politicas de los administradores de la AS.
2. Se quedan con las rutas que la lista *AS-PATH* es la mas corta.
3. Utilza el mismo criterio que el *Enrutamiento de la patata caliente*. 
4. Utiliza *indicadores BGP* para seleccionar una ruta. [Ni idea que es esto]

## Ip-Anycast 
BPG se puede utilizar para implementar de forma natutal un IP-Anycast. 
La idea de anycast es que varios servidores tengan la misma ip, pero al enviarle un mensaje, este llega al mas adecuado de ellos. 
Esto nos interesa ya que:
- Nos permite distribuir la carga entre varios servidores, duplicando su contenido
- Cada Host se conecta con su servidor mas cercano
La forma en la que se resuelve esto con BGP es natural. Como cada servidor tiene la misma IP, los distintos ruters ven esto como distintas rutas, y se quedan con la mejor, por lo que los paquetes solo se enrutan hacia es mejor cantidado. 

Esto es muy utilizado para DNS. 

