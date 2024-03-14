Contamos con los siguientes elementos básicos:
- `Modelo de aplicación`
- ``Programa de Aplicación``
- ``Bibliotecas grafica``
El `modelo de aplicacion` contiene los datos de la aplicación, luego el `Programa de aplicacion` es el programa el cual utiliza fuertemente los gráficos para su operativa. En ves de programar el componente grafico dentro del programa, se crea una `bibloteca grafica`. Esta ultima es quien tiene el control de los gráficos y también el control y traspaso de datos de los *dispositivos de salida* y los de *dispositivos de entrada*
Ademas se definen dos ductos:
- ``Ducto de salida``: Es el flujo que se tiene desde los datos hasta que se expresa en dispositivos de salida (como una impresora grafica o monitor)
- ``Ducto de entrada``: Es el flujo que se tiene desde los dispositivos de entrada hasta los datos del modelo o programa. 

Luego hay dos posibilites
- Uso del `Modulos de discretizacion`: Se usan módulos especializados en las operaciones de la bibliotecas grafica, estos módulos son a bajo nivel, ejemplo como renderizar una lineal en los pixeles, y luego deja los resultados en en la `memoria grafica`. Notar que aqui todo el procesamiento lo realiza el CPU. - ![[Pasted image 20240310021558.png]]
- Cuando hay un `Procesador grafico` (GPU): Se envian instrucciones (primitivas + atributos) para que el ``controlador`` del `Hardware grafico` realice la operacion.![[Pasted image 20240310021611.png]]
