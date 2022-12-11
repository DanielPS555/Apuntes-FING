Un sistema con switches comun y corriente (en forma de arbol por ejemplo) tiene algunos problemas:
- `Falta de aislamiento del trafico`: Todas las tramas de difusion viajan por toda la red. Lo aumenta el trafico y afecta el rendimiento de la LAN,
- `USo ineficiente de los switches`: Podemos tener pocos usuarios por switch, los cuales los queremos tener separados de la misma dominio de difucion. Sino se podrian poner todos en el mismo switch, pero no quedarian aislados. 
- `Gestion de usuarios`: Nos complica mover un usuario de un grupo a otro, ya que se tiene que cambiar el cable. 

Las *VLAN* solucionan esto. Las VLAN permite definir multiples redes de area local virtuales sobre la infraestructura de una unica red LAN fisica. 
Los costos de una misma VLAN se comunican entre si como si estubieran ellos solo en el switch, lo que genera un dominio de disfusion. 

Se seleccionan los puertos del switch al que queramos que pertenescan a una misma VLAN. 
Internamente estos switches tiene una tabla de correspondencia entre los puertos y las VLAN a la que se lo agrego. El router solo puede redirigir una trama de un puerto de una VLAN a otro puerto de la misma VLAN. 

Si queremos conectar dos dispositivos que tiene muchas VLAN, se utilizan la tecnica de *troncalizacion*, donde los switches por ejemplo se conectan entre si por un unico puerto (enlase troncal) y las tramas que viajan por ahi puede corresponder a diferentes VLAN de los switches (o routers ) conectados. Estas tramas tiene la forma de *802.1Q*, donde la trama es muy parecida, solo que luego de la dirrecion de origen se le añade unos 4 bytes. 
- *Identificador del protoclo* (2 bytes): Identifica al protoclo, tiene un valor fijo de 81-00 en hexadecimal. 
- *Informacion de control de etiquetado* (2 bytes): Tiene dentro un campo que identifica la VLAN espesifica (12 bits) y otro de 3 bits que identifica la prioridad. 
![[Pasted image 20221116233821.png]]

Las VLAN tambien se pueden definir por MAC en vez de por puerto. Hay otras formas que incluso tocan la capa de red. 
