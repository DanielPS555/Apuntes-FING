# Capa de protocolos
Los protocolos de dividen en varias capas, esta arquitectura permite que los protocolos de una capa N pueda utilizar los protocolos de la capa N-1. 

Se le llama *pila de protocolos*  a un conjunto de protoclos de distintas capas. En particular si tomamos la pila de protoclos que forman internet, podemos encontrar 5 capaz:

- `Capa de aplicacion`: En esta capa es donde residen las aplicaciones y sus protoclos. A los paquetes de la capa de aplicacion se los llama *mensaje*
- `Capa de transporte`: Esta capa es la encargada de transportar la informacion de una aplicacion de un host a otro host. Los paquetes en esta capa se llaman *segmentos*
- `Capa de red`: Esta capa es la responsable de trasladas sus paquetes, llamados *datagramas,* al otro host. Para eso utiliza el protocllo IP, y protoclos de enrutamiento. 
- `Capa de enlase`: Esta capa es la encarga de transportar los paquetes llamados *tramas* desde un nodo al siguiente en la ruta.
- `Capa fisica`: Su trabajo consiste en mover los bit de la trama de un nodo a otro por el canal. 

Un concepto importante del esquema por capaz es el de *encapsulacion*. Donde a medida que un paquete baja entre capaz, la capa inferior encapsula el paquete de la capa superior, añadiendole al mismo una cabezera propioa. Por lo que cada paquete de cada capa tiene dos componentes: *campos de cabezera*, que tiene la informacion aportada por esta capa, y un campo de *carga util* que por lo general es el paquete de la capa superior. A medida que el paquete se mueve por la red y en los distintos dispositivos va subiendo y bajando de capa, la informacion de una capa que no se haya recorrido, no sera alterada, por ejemplo solo el host de origien y destino llegan a tomar un paquete y llevarlo hasta la capa de aplicacion, por lo que nadie en el medio modificara la el mensaje. 