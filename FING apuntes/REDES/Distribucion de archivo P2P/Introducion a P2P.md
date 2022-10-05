# Introducion a P2P

P2P es un *tipo de arquitectura* donde la dependencia con un servidor es inexistente o directamente minima. Por otro lado un conjunto de host se conectan entre si directamente. A esos host se los conoce como *peer*.

En la distribucion de archivos utilizando una arquitectura cliente-servidor, el servidor tenia que enviar una copia del archivo a cada uno de sus clientes, lo que aumentaba la carga del servidor muy rapidamente y por ende su ancho de banda. 
Por otro lado en la arquitectura P2P cada peer utiliza ancho de banda de subida para poder distribuir distintas partes de los archivos a los demas peer. 

## Compracion de velocidad entre cliente servidor y P2P

Supongamos que un archivo de tamalo `F` inicialmente lo tiene unicamente el servidor, tenemos N host (sin contar al servidor), cada servidor tiene una velocidad de carga $u_i$ y una velocidad de bajada de $d_i$. 

Definimos $D_{cs}$ como el tiempo de distribucion del cliente-servidor y el $D_{p2p}$  como el tiempo de distribucion de P2P.

Obtenemos las siguientes cotas (Mirar de donde salen en la pagina 117-118 del libro)

$D_{cs} \geq max\{ \frac{NF}{u_s}, \frac{F}{d_{min}} \}$ con $d_{min} = min\{d_1, .... , d_N\}$

$D_{P2P} \geq max\{ \frac{F}{u_s}, \frac{F}{d_{min}}, \frac{NF}{u_s + \sum_{i=1}^{N} (u_i) } \}$ con $d_{min} = min\{d_1, .... , d_N\}$

Se puede probar que esos mayores iguales en determinadas distribuciones se alcansa la igualdad, en esos casos se puede observar este comportamiento:

![[Pasted image 20221004163220.png]]







`
