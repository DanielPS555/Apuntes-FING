
- En este cap se explica el rol del testing dentro del ciclo de vida de desarollo. Sea una el modelo en V como guia. 
- Cada ciclo de vida muestra una perspectivadel testing
- El modelo en V muestra que el testing es tan importante como el desarrolo. 

## Modelo en V
- La idea de este modelo es que el las actividades de desarrolo y testing tiene igual importancia. 
- La  rama isquierda muestra el proceso de desarrolo
- La rama derecha muestra el proceso de intergacion y testing. Este ultimo *finaliza* con las *pruebas de aceptacion*.
- El modelo en V es como el que sigue: [Añadir foto]
- Las partes son: 
	- **Requierement definition**: Las necesidades y requerimientos son recolectados, espesificados y aprobados. 
	- **Functional system design**: Se mapean los requerimientos con las funcionalidades 
	- **Technical system design**: Se diseña la implementacion del sistema. Ej interfaces, componentes (arquitectura.  
	- **Component specification**: De espesifica a detalle cada componente. 
	- **Programming**
	- **Component test**: Se verifica que cada componente cumple su espesificacion
	- **Integration test**: Se verifica que grupos de componentes interactuan de la forma que deberian 
	- **System test**: Se verifica que el sistema como un todo cumple con los requerimientos espesificados.
	- **Acceptance test**: Se verifica si el sistema cumple con los requisitos en el contrato y/o con las necesidades y expectativas del usuario.
- Por lo general *los fallos son encontrados* con los *test en el mismo nivel de abstracion*
- La *validacion* es el proceso de chequear que el resultado de desarrolo contra sus requisitos originales. Cuando se valida se jusga si el producto (parcial o completo) *soluciona la tarea y si cumple con el uso esperado*. Se *investiga* si el sistema tiene sentido en el contexto de uso esperado.
- La *verificacion* es el proceso de chequear que la salida de ese nivel de desarrolo haya sido obtenida correcta y completamente de acuerdo con el input de ese nivel de desarrolo. Aqui se verifica la correctitud y completitud de la fase, no si el producto es util en el contexto de uso.
- En el modelo en V, *no es verdad que el desarrolo comienza tarde* . El nivel de testeto del lado derecho corresponde a un nivel de execucion del testing, por ejemplo test planning y test analysis and design se puede hacer en paralelo al proceso de desarrolo. 
- La sepracion entre los niveles de testeo no es solo temporal, sino una sepracion tecnica, por lo que cada nivel requiere personal, conocimiento y objetivos diferentes.

## Component test
### Explicacion de terminos
