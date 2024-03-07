Libro del curso = Guid to Computing Fundamental in cyber Physical systems


## Notas de la presentacion

- Los sistemas cyber fisicos son la utlima etapa en la evolucion de la computacion
- ![[Pasted image 20240307015708.png]]
- **Son Sistema re-alimentado**: El sistema le envia a una unidad de control la informacion para que el sistema de ajuste lo mas posible a la salida buscada.
	- El sistema funciona en tiempo real (tiene exigencias en cuanto a los tiempos de respuestas)
	- Son sistemas inteligentes, adaptativos y predicticos. 
	- Posiblemente sean sistemas con internet y capaz distribuidos. 
		- Posiblemente mida el entorno fisico para realizar una accion.
- **Requieren ser**
	- Tener seguridad (ataques)
	- Ser sistemas seguro (que no puedan hacer daño)
- Existen múltiples *metodologias* de diseño de estos sistemas. 
	- La biónica ha hecho grandes aportes a las metodologías de diseño.
	- Estas metodologias deben soportar 3 cosas: 
		- Espesificacion, modelado y analisis
		- Manejo de la escalabilidad y complejidad
		- Validacion y verificacion. No puede ser solo testing, tiene que ser una mezcla entre un punto formal y testing


## Que es CPS

- ``Cyber``: De computacional, control discreto, lógica 
- ``Physical``: Hecho por humanos que esta gobernado por las leyes de la fisica y opera en tiempo continuo
- Cyber-Physical= Sistema *altamente integrago* entre lo Cyber y lo Phsical en mukltiples niveles y escalas
- Integracion con network computing
- Muchos campos de aplicacion
- Tiene una gran relacion con la industria 4.0

- Se tiene sistemas automatizados para la produccion y espesificacion de productos a los proveedores
- Se tiene sistemas de simulacion de los sistemas a desarrolar

- Los sistermas `abiertos` son aquellos que se pueden re-configurar

- Es una confluencia entre multiples areas, algunas de ellas son: 
	- Embedded Systrems
	- Real time
	- Wireless Sensor Networks
	- Control
- En los sistemas ciber fisicos es fundamental el *manejo del tiempo*

- A medida que se sube en el nivel de abstracion, es mas complicado poder garantizar las exigencias de tiempo y concurrencia
- Muchas de la implementacion de hardware y sistemas para tiempo general, no sirven para tiempo real. Ejemplo procesadores que tiene pipelines y cosas asi. 
- las partes criticas tiene que estar aisladas
- Hay mucho trabajo hoy en dia que intentar garantisar entrega en tiempo por internet


## Sensor y actuadores
Sensor: mide una magintud fisica
Actuador: Modifica una magnitud fisica
[Falta mucho]


## Redes
Ethernet
CAN 
TTP 
FlexRay
TTEhternet
TSN
