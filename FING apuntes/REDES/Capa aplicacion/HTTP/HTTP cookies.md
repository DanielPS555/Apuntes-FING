# HTTP cookies
Como se menciono HTTP es un *protocolo sin memoria*, por de por si no hay forma de saber que le respondimos a cada usuario. Y menos si recivimos nuevamente una peticion de este host.

Para solucionar este problema se inventaros las *cookies*. Estas sirven para identificar al usuario. 


## Funcionamiento
El funcionamiento es simple, cuando recivo una peticion sin la linea de cabecera *Cookie*, genero un nueva cookie (un codigo), y lo guardo en la base de datos backend. Luego le devuelvo por la la linea de cabecera *Set-cookie* esa nueva cookie generada. El navegador guarda esa cookie asociada a sito web. Por ultimo cada vez que el usuario navega por esa pagina, el navegador añadira la linea *Cookie* con la cookie que dicha pagina alguna vez nos envio y nosotros guardamos. 

## Requerimientos para implementar cookies
1. Una linea de cabecera de las HTTP responce llamada *Set-Cookie*
2. Una linea de cabecera de las HTTP request llamada *Cookie*
3. Un archivo de cookies almacenado y manejado por el navegador(s) en el host cliente 
4. Una base de datos backend que se encarge de almacenar las cookies y lo referido a estas.