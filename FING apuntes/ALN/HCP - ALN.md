
## Ordenes
- Denominamos $T(N)$ al tiempo de ejecucion de un programa
- Denominamos al *Orden* $O(n)$ de un algoritmo como una funcion $f$ tal que, dado una constante $c$ se cumple que $c*f(N) > T(N)$
	- Entonces Si $T(N) = 2N^2$ entonces $O(N) = N^2$
- Notar que $O(n)$ solo mide el numero de operaciones a realizar, no tiene encuentra temas como localidad, acceso a memoria, etc

## Evaluación de desempeño
- $Cpu\_Time = NI * CPI * CCT$
	- NI = numero instrucciones
	- CPI = Numero de ciclos de reloj por instruccion
	- CCT = Tiempo del ciclo de reloj
- MIPS = Numero de millones de  instrucicones por segundo
- $MIPS = \frac{Frecuencia\_reloj} {CPI * 10^ 6*}$
- El tiempo del proceso se divide en:
	- *Tiempo de usuario*: Tiempo en que se dedica a operaciones de usuarios
	- *Tiempo de sistema*: Llamas al sistema
- **Tiempo de CPU**: Tiempo en que la CPI esta ocupada ejecutando instrucciones del proceso.
- **Walltime**: Tiempo *real* que transucrre entre un evento y otro. [Duda: Que eventos]

- Se puede evaluar el desempeño mediante el uso de *benchmarks*
- **Micro benchmarks**: Diseñados para medir el desempeño de un codigo pequeño , o para medir determinadas features del hardware. Por ejemplo:
	- Velocidad de procesador
	- Acceso a memoria
- **Kernel benchmarks**: Son un conjunto de rutinas simples para evaluar el desempeño del hardware  y compiladores [Duda: No me  queda tan claro como seria esto]
	- EJ: # Livermore loops

## Von Neumann
- Las maquinas de Von Neumann  tiene el siguiente formato:
- ![[Pasted image 20230820224852.png]]
- M = Memoria
- CC = Unidad de control, controla el comportamiento de la CPU
- CA = Unidad aritmética y lógica de la CPU
- I/O = Entrada y salida

- Para cada programa hay un **Contador de programa** el cual indica la siguiente instruccion a ejecutar. Luego se aumenta el contador. 
- Dicha instrucción es traída de memoria principal y *decodificada de la unidad de control*. 
- Posteriormente se ejecuta la instrucción.  


## Pipeline
- La unidad funcional se divide en sub-unidades funcionales
- Un *pipeline básico* divide el ciclo de una instrucción en dos etapas: 
	- *Fetch*: Traer la siguiente instrucción desde memoria
	- *Execute*: Ejecutar la instrucción
- Notar que cada etapa es realizada por una unidad funcional diferente  
- Un pipeline mas avanzado podria ser: 
	- *FI*    - Fetch de una instrucción
	- *DI*   - Decodificar instruccion
	- *CO*  - Calcular los operandos
	- *FO*   - Fetch de los datos
	- *EI*     - Ejecutar instrucciones
	- *WO*  - Escribir en la memoria
- Algunos problemas de los pipelines:
	- Se puede llenar el pipeline
	- **Hazards** (Obstaculos)
		- Puede ocurrir que en un mismo paso, dos pasos del pipeline no se puedan ejecutar correctamente en simultaneo. Algunos motivos pueden ser: 
			- Bifurcación en el código
			- Dependencia de datos
			- Conflictos de hardware
		- En estos casos puede ser necesario detener el pipeline o vaciarlo. 
		- Hay formas de poder disminuir la ocurrencia o penalización de los mismos. 
- **Latencia**: Tiempo en que se procesa una tarea
- **Throughput**: Rendimiento, medido en tareas o unidades procesadas por tiempo.
- Notar que el pipeline no afecta la latencia, pero si el Throughput. 
- Aumentar el numero de pasos mejora la *aceleración* , del pipeline, mientras que un desbalanceo lo disminuye

- Incluso para mejorar un pipeline se puede paralelizar algunas etapas. Por ejemplo paralelizar la suma en punto flotante

-  Se pueden combinar diferentes pipelines, de forma tal que la salida de uno sea la entrada del otro.
	- EJ: Multiply-accumulate : $a = a + bc$

## Maquinas vectoriales
- Aqui las instrucciones operan sobre arreglos de largo variable
- Los registros tambien son vectoriales 
- Se usan poco, muy caras
- Las GPU emplean esa idea

## Estrategia de compilacion
- Hay muchas estategias que pueden emplear los compiladores
	- Estas estrategias permiten aplicar algunas optimizaciones o complicar para una arquitectura en particular.
- Algunas estrategias: 
	- *Optimizaciones*: -O0, -O1, -O2, -O3, -Ofast
	- *-x{code}:* permite generar código específicamente para los CPU indicada por ``code``
	- *-xHost*: Genera código con el set mas alto disponible en el host
	- *-mtune=cpu*: Optimiza el código para una ``cpu`` especifica
	- *Optimizacion interprocedural*: [Duda: investigar mas de eso]
	- Punto flotante
		- *-fp-model {Fast | Precise | Source | Strict}*
		- *-pc{32|64|80(defualt)}*: Prcision interna de la FPU (unidad punto flotante)
		- *-rcd*  y *--fp-port*: Controla utilización de redondeos y truncamientos
	- *-openmp*: OpenMP permite programar paralelismo en memoria compartida
- Hay algunas practicas que pueden permitir al optimizar realizar su tarea de mejor forma:
	- Minimizar la utilización de variables globales 
	- Evitar el uso de controles de fujo complejos
	- No usar instrucciones cast
	- Evitar las referencias indirectas 
	- *Fetch scheduling* - Mayor info en PDF
	- *Loop unrolling* - Mayor info en PDF
	- *Scalar expansion* - Mayor info en PDF


## Memoria
- Hay muchos tipos de memoria dependiencio de aspectos como: Costo, tamaño, velocidad, etc. 
- Jerarquia de memoria:
	- Registro
	- Cache (2 o 3 niveles)
	- RAM
	- Disco
	- Almacenamiento remoto
- **Principio de localidad**: Los programas tiene a acceder a instrucciones cercanas o recientes a lo que se accedió recientemente. 
	- **Localidad temporal**: Un item referencialo tiene a volver ser referéncialo nuevamente a la brebedad
	- **Localidad espacial**: Los item con dirección cercana a un item recientemente referenciado tiene a ser referenciado a la brevedad. 

#### Cache
- Memoria pequeña y rápida, entre el procesador y la memoria principal, diseñada para aprovechar el principio de localidad
- **Cache Hit**: El registro buscado se encuentra en cache
- **Cache Miss**: El registro buscado no se encuentra en cache
- LA cache tiene *tags* para identificar los bloques de memoria principal que se encuentran en cada linea de la cache 
- Para mejorar el rendimiento de una cache se puede:
	- Reducir el miss rate
	- reducir la penalizacion de miss
	- Reducir el tiempo de busqueda de la cache (tiempo de hit)

#### Memoria virtual
- La memoria RAM es limitada, por lo que se utiliza el disco para aumentar el espacio de memoria. La informacion se trae del disco con unidades de *page*
- **Page Fault**: Es cuando se busca un registro que esta en una pagina que no se encuentra en RAM