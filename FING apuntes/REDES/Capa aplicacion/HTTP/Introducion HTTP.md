# Introducion HTTP

HTTP es uno de los principales protocolos utilizados en la web. Se un protoclo con *arquitectura cliente-servidor*. 
Se puede utilizar para obtener recursos de un servidor HTTP.

En la arquitectura, los clientes HTTP son por lo general los *navegadores*, y los servidor HTTP son los *servidores web*.

Para obtener un objeto via HTTP se requiere una URL (Tambien el metodo HTTP, eso lo vamos a ver en [[Formato del HTTP]]), la url tiene dos partes, la primera es el *nombre del host* que alverga el recurso, y luego esla *ruta del recurso* que se quiere obtener. 

Cuando el cliente requiere de un objeto (por ejemplo una pagina web) realiza una *HTTP request* , solicitando el recurso, luego el servidor le contestara con una *HTTP responce*. 

HTTP tiene la caracteristica que es un *protocolo sin memoria* osea, no mantiene informacion de a que host les contesto, para eso se van a utilizar las [[HTTP cookies]]. 


**Importante**: HTTP funciona con *TCP* y generalmente escucha el puerto *80*. Si es *HTTPS* sera el puerto *443* 

