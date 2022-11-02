Los algoritmos de enrutamiento seran los encargados de determinar buenas rutas entre el emisor yu el receptor. Considerando los costes y algunas restriciones externas. 

Sin importar si es por control de router o logicamente centralizado, se debe definir routas claras para los paquetes. 

Los algoritmos de enrutamiento se pueden dividir en varios tipos:

**Algoritmos de enrutamiento segun su conocimiento**
- -``Algoritmo de enrutamiento centralizado`` : Ese conoce todos los nodos y costos de toda la red. Se puede utiliar en sistemas SDN por ejemplo. Los algoritmos de esta caracteritica se los conoce como *algoritmos de estado de enlase* (LS - link-state)
- ``Algoritmos de enrutamiento decentralizados``: Cada router solo concoe a sus vecinos y los costos de sus enlases. Por lo que la ruta se calcua de forma distribuida. Un algoritmo sus famosos algoritmos de lo conoce como *algoritmo de vector de distancias* (DV, Distance-vector)

**Algoritmos de enrutamiento segun la frecuencia de cambios**
- `Algoritmos estaticos`: Las rutas cambias lentamente, generalmente porque un humano toco algo
- `Algoritmos dinamicos`: Modifican sus rutas a medida que cambia la carga de trafico o la topologia de la red. **Importate:** son suspetibles a problemas de *blucle de enrutamiento* y *osiciacion de rutas*

**Algoritmos de enrutamiento segun su sensibilidad a la carga**
- `Algoritmo sensible a carga`: Varian los costes de los enlases segun la carga, de forma de traajar con la congestion. No se usan hoy en dia
- `Algorimo no sensible a carga`:  No reflejan en el coste del enlase no refleja el nivel explcito de congestion.


## Algoritmo de enrutamiento de estadso de enlase (LS)
Para utilizare esos algoritmos, los routers envian *paquetes de difucion* en el cual informan a los demas routers de sus vecinos y costos de enlase. Utilizando *algoritmos de difucion de estado de los enlases* se consigue que todos los routers conoscan todo el estado de la red, dando asi una vicion completa e identica entre ellos. 

Uno de los algoritmos mas conocidos para un link-state es Dijkstra, su ejecutcion mirala en el libro. 

Lo importante es que bien implemetado tiene un orden de $O(log(n)n)$ . 

Este algoritmo utiliza como metrica de enlase la congestion y retardo. Por lo que puede sufrir de lo que se conoce como *osiciacion de rutas*. Eso sucede porque todos terminan sincronisandose y calculando la ruta de sus paquetes al mismo tiempo, por lo que los cambios se hacen todos en la misma dirrecion, lo que termina concentrado todas las rutas en los mismos enlases, por que proboca mas congestion y genera que cambien a la vez de nuevo todas sus rutas (y asi infinitamente). 
La solucion mas razonable es hacer que los router no ejecuten su algoritmos al mismo tiempo,. Para evitar que los router se auto-sincronizen, lo que se puede hacer es que envien aleatoriamente su anuncio. 

## Algoritmo de enrutamiento por vector de distancias (DV)