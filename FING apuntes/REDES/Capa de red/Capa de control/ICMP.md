- ICMP es un protoclo de capa de red, que se utiliza para poder intercambiar informacion de *control  de internet* entre los routers y los hosts. 
- Los mensajes ICMP son transportados dentro de datagramas IP
- El numero del protoclo de capa superior que usa IP para referenciar a ICMP es 1
- Hay implementacion que podrian permtir el contol de congestion mediante mensajes ICMP de los routers, aunque se usa poco. 

![[Pasted image 20221201170837.png]]


![[Pasted image 20221201170846.png]]

ICMPv6 introduce nuevos codigo y tipos. Por ejemplo hay uno llamado "Packt too big" que se utiliza para calcular el MTU path de una routa a la hora de fragmentar ipv6. 