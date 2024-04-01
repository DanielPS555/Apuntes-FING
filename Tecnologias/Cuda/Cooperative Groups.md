Fuentes: 
- https://developer.nvidia.com/blog/cooperative-groups/


Importación: 
```c++
#include <cooperative_groups.h>
```


Todos los data types y interfaces estan definidas en el siguiente `namespaces: cooperative_groups` 

Se puede usar las siguinetes estrategias: 

```c++
using namespace cooperative_groups;

using cooperative_groups::thread_group;

namespace cg = cooperative_groups;

```


## Thread Groups

- `unsigned size()` - Para obtener el tamaño del grupo de thread
- `unsigned thred_rank()` - Retorna el indice del hilo actual dentro del grupo de thtrad.


## Sync
Sync es una `collective operation` que permite la sincronizar dentro del grupo. 

Por ejemplo si tenemos un grupo de thread llamados `g`, entonces `s.sync()` espera a que todos ellos lleguen a la llamada del sync para continuar. 

Ejemplo con una reducción de suma: 
```c++
using namespace cooperative_groups;
__device__ int reduce_sum(thread_group g, int *temp, int val)
{
    int lane = g.thread_rank();

    // Each iteration halves the number of active threads
    // Each thread adds its partial sum[i] to sum[lane+i]
    for (int i = g.size() / 2; i > 0; i /= 2)
    {
        temp[lane] = val;
        g.sync(); // wait for all threads to store
        if(lane<i) val += temp[lane + i];
        g.sync(); // wait for all threads to load
    }
    return val; // note: only thread 0 will return full sum
}
```



## Particionando grupos

Se pueden particular grupos (`tile`) en grupos mas pequeños. Esto permite cambiar la perspectiva desde donde se ve el grupo. 

Por ejemplo

```c++
thread_group tile32 = cg::tiled_partition(this_thread_block(), 32);
````

En anterior comentado toma el bloque actual de ejecucion del bloque y genera `tile` de 32 threads (un warp). Notar que todas las intrucciones que hemos usado (ejemplo: sinc, thread_rank tambien aplica a este nivel.

Ejemplo de uso:

```c++
thread_group tile4 = tiled_partition(tile32, 4);
if (tile4.thread_rank()==0) 
printf("Hello from tile4 rank 0: %d\n",
       this_thread_block().thread_rank());
       
```
Salida:
```
Hello from tile4 rank 0: 0
Hello from tile4 rank 0: 4
Hello from tile4 rank 0: 8
Hello from tile4 rank 0: 12
```

También se puede realizar esta operation de forma `static`, eso mejora la performance. Aquí esta como se realiza:
```c++
thread_block_tile<32> tile32 = tiled_partition<32>(this_thread_block());
```

## Warp-Level Collectives
Se pueden usar las operaciones a nivel de warp para sincronizacion:
.shfl()  
.shfl_down()  
.shfl_up()  
.shfl_xor()  
.any()  
.all()  
.ballot()  
.match_any()  
.match_all()


## Coalesced Thread
Cuando ocurre una diverengia, solamente algunos de los thread del warp quedan activos. Podemos obtener estos thread en un grupo usando:
```c++
 coalesced_group active = coalesced_threads();
 ```
 Eso nos devuelve el grupo de los `coalesced_threads`, o sea los thread activos dentro del warp luego de la ramigicacion. Notar que jamas nos retorna mas que un warp.
 Esto puede ser util para una sincronizacion dentro de un if que genero  divergencia. 