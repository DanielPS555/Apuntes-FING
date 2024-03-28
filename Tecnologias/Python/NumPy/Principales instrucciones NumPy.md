- `np.__version__`
- `np.array()`
	- Ej: np.array([[1,2,3],[4,5,6]])
	- Ej: np.array([[1,2,3],[4,5,6]], dtype=np.float32)
	- Tipos: [Data types — NumPy v1.26 Manual](https://numpy.org/doc/stable/user/basics.types.html)
	- Podes crear de dimencion 0 si pones un valor unitaroio (ejemplo un numero). Ejemplo np.array(3)
- INSTANCIA.``dtype``
- INSTANCIA.shape = (\#filas,\#columnas)
- INSTANCIA.ndim = numero de dimenciones
- INSTANCIA.size = numero de elementos

## Acceder a las estructuras de datos
Se pueden acceder a las estructuras de datos

[Completar]

#### Mascaras


## Generar Elementos

#### Generar matrices
- `np.ones( (dimencion_x, dimencion_y))`
- `np.zeros( (dimencion_x, dimencion_y))`
- `np.eye( dimencion_x, dimencion_y = None)`
- `np.diag( lista_a_diagonalizar)`

#### Generar vectores
- `np.arange(inicio, fin, offset)` No incluye el final
- `np.linspace(inicio, fin, numero_elementos)`

## Funciones universales y broadcasting
axis = columnas
axis = fila



## Algebra

Muchas de estas funciones se encuentran en el paquete `numpy.linalg`

- `transpose()` o INSTANCIA`.T`  - Transponer la matriz
- `@` o `np.dot`
	- OJO: Con vectores es el producto interno
- `np.linalg.norm` - Calcula la norma (Por defecto la de Frobenius $\sqrt{\sum_{i,j}A_{i,j}^2}$ .)
- `np.linalg.eig` - calculo de valores y vectores propios

## Reshaping

- INSTANCIA.`reshape(nueva_dim_x, nueva_dim_y)`
- `np.concatenate((array1,array2))` - Permite concatenar, cuidado que al cambiar el tamaño es costosa de computar. 
	- Se puede especificar un `axis` para decir con que concatenar: O sea `axis = 0` para concatenar las columas (hacer el largo de las columnas mas grande), o `axis = 1` para concatenar las filas (hacer las filas mas grandes)


## Polinomios
- `np.roots(coeficientes)` - Nos da las raíces de un polinomio cuyos coeficientes se especifican en un lista. Ejemplo $np.roots([2,0,1])$ nos retorna las raíces del polinomio $2x^{2} + 1$
- `np.poly(raices)` - Nos retorna los coeficientes de un polonio cuyas raíces son las especificada en los parámetros de la función.
- `np.polyval( coeficientes, preimagen)` - Dado los coeficientes de un polinomio y una pre imagen computa de forma eficiente la imagen.  
- `np.polyfit(cordenadas_x, cordenadas_y, grado_polomio)` - Calcula el polinomio de interpolación que mejor aproxima a un polinomio de grado especificado (según la función de costo mínimos cuadrados) a los puntos espesificados con la lista de cordenadas_x y las cordenadas_y. Ejemplo de llamada: $np.polyfit([0,1,2.1],[0,1.2,4.1],2)$


## Numeros aletorio


## Tensores

> Todas las operaciones que veremos pueden extenderse a arrays de mayor dimensión