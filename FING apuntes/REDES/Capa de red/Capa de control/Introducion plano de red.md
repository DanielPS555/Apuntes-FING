
> plano de control: la lógica de la red que controla no solo cómo se reenvía un datagrama
de un router a otro, a lo largo de una ruta extremo a extremo desde el host de origen al host de
destino, sino también cómo se configuran y gestionan los servicios y componentes de la capa de red.

Tenemos dos algortmos de enrutamiento que son *OFPF* y *BPG*.

En el plano de datos nos enfocamos como se trataban los paquetes en base a las tablas de reenvio y flujo. En el plano de control veremos como determinarlas y mantenerlas en los routers. 

Hay dos posibles enfoques: 
- `Control por router` Cada router tiene su algoritmo de enrutamieto, y calcula su tabla de re-envio si mismo. Los protoclos OSPF y BGP funcionan con este enfoque
- `Control logicamente centralizado` Todo lo que refiere al control de las tablas de reenvio o flujo es calculado y distribuido por un controlador centrla. Luego cada router tiene un *agente de control*  (AC) que se conecta con el controlador central y ejecuta lo que este le dice.  