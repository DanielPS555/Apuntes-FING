# Formato de los mensaje HTTP

En este apartado vamos a ver los formatos de los mensajes HTTP. 

## Mensaje de solicitud
- Estos mensajes son enviados en codigo ASSIC, por lo que a menos que se encripten se pueden leer. 
- Comienza con una *linea de solicitud*, que esta formada bajo el siguiente formato:
	*Metodo, Recurso, version HTTP*
- Los metodos posibles son *GET, POST, PUT, HEAD Y DELETE *
- Luego las demas lineas se llama *lineas de cabecera* , hay muchas posibles de estas lineas, algunas que siempre deberian estar son:
	- *Host*
	- *Connection*
	- *User-agent*
    Tambien puede haber otras lineas que se utilizan, algunas de estas son:
	- *Accept*
	- *Accept-languajes*
	- *Cookie*
	- *Content-Ecoding*
  
- Cada linea de solicitud termina en un retorno de carro y un salto de linea. Luego de la ultima linea de cabesera, se imprime una linea vacia, que termina nuevamente con el retorno de linea y el salto. 
- Opcionalmente mensajes de solicitud pueden llevar un *objeto* si tiene el metodo POST o PUT
- El *HEAD* funciona igual al *GET* con la diferencia que el servidor omite devolver el objeto de solicitado, solamente devuelve las lineas de cabecera. 
 ![[Pasted image 20221003021447.png]]


## Mensaje de respuesta
- Los mensajes de respuesta son muy similares, la diferencia fundamental esta en que ahora la primera linea sera una *linea de estado*, luego tendremos *lineas de cabecera* que algunas diferentes a la de la solicitud y por ultimo un objeto que la pagina podra o no devolver. 
- La *linea de estado* tiene esta forma *Version de HTTP* , *Codigo de respuesta* y *Mensaje de respuesta*
- Algunos de los posibles codigos de respuesta son los siguientes:
	- 200 = OK
	- 202 = aceptado (recivi la peticion, pero aun no actue)
	- 301 = Moved Permanently (Movie el objeto a otro lugar y en la linea de cabecera Location te paso su nueva URL)
	- 304 = Not Modified (Utilizado para las [[Almacenamiento en cache HTTP]])
	- 400 = Bad request
	- 401 = No autentificado
	- 403 = No autorizado 
	- 404 = Not found
	- 500 = Internal server error
	- 505 = Version no soportada
- Algunas lineas de cabecera importantes: 
	- *Last-modified* : fecha de la ultima modificacion
	- *Content-Length* Tamaño del objeto, muy importante para distinguir cuando un mensaje HTTP termina y comienza el siguiente en una stream TCP. Osea con HTTP persistente
	- *Content-Ecoding*
	- *Content-Type*
	- *Server* : nombre del tipo de servidor que contesta
	- *Last-Modifed*
	- *Connection* : Devuelve close si luego de este mensaje cierra la conexcion.
	- *Set-cookie*: Por aqui se devuelve una nueva cookie creada para esta seccion

Las lineas de cabecera son puesas por el navegador/servidor dependiendo de la situacion, poca de ellas pueden ser determinas por nosotros. 