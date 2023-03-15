DUDAS: 
- Las stories changes son para reportar nueva funcionalidad o bugs unciamente?

# Introduccion

- Actualmente la mayor prioridad en el mundo del software es la rapides. Incluso se permite cabiar calidad y funcionalidades por velocidad de liberacion. 
- En etse mundo cambiante los clientes les es imposible predecir los requerimienos, los mismos cambian muy rapidamente. Capaz nisiquiera los clientes los conoscan hasta luego que el programa este operativo. 
- Debido a esto, un modelo es casada no es adecuado.
- Para el mundo empresarial, los modelos enfocados en la velocidad son esenciales, a estos se los conoce como *rapid software development* o tambien *agile development*. 
- Estos se diseñaron con el propocito de diseñar software usable rapidamente. 
- Los metodos agiles comparten algunas caracteristicas. 
	1. El proceso de espesificacion, diseño e implementacion esta intercalados. No hay un detallado *system specification* y la *documentacion es minima* o *generada automaticamente*.
	2. El sistema se desarrola *incrementalmente*. Los interesados *participan en la evaluacion y definicion del incremento*. 
	3. Se utilizan un conjunto de *heramientas* para apoyar el desarrolo. 
- Los incrementos son *pequeños* y se hacen cada *2 o 4 semanas*. Se involucan a los *clientes* para conseguir *feedback* rapidamente o *cambios en los requerimientos*.
- Se utiliza *informan communication* en vez de comunicacion formal o documentacion
- En las metodologias agiles, las *actividades central son el diseño y la implementacion*.
- En el desarrolo agil, las *actividades se desarrolan* an paralelo, por lo que el diseño y y la programacion se dan en paralelo. 

[Mirar figura 3.1]


# Metodologias agiles
- Los *plan-driven* tiene un gran *sobrecosto* en la: Planificacion, Diseño, Documentacion
	Por lo general este sobre costo esta justificado en los siguientes casos:
	- Desarrolo con *multiples equipos cordinados*
	- *Sistemas criticos*
	- Cuando el sistema es muy duranble en el tiempo y *multiples personas participaran del mantenimiento* a lo largo del tiempo.
- En la metodologia clasica *se tarda mas tiempo con tareas de como programar que programando y testeando*. Ademas cuando cambian los requerimientos, el diseño y la espesificacion de diseños requieren un *rework*.
- La idea con esta metodologia es *rapidamente* liberar  *software usable*. Obtener nuestros requerimientos de los clientes e incluir estos cambios en *iteraciones futuras*
- La idea es *eliminar procesos burocraticos* que tiene un efecto dudoso a largo plazo. Y *documentacion* que posiblemente nunca se use.

#### Principos de la metodologia agil
[Poner la cita del manifuesto de la metodologia agil]

Los principios de la metodologia agil son: 
- `Customar involment`: Los *clientes* tiene que estr *incluidos en el proceso de desarrolo*. Su rol es *brindar* y *priorisar requerimientos*. Tambien *evaluar* la iteracion del sistema.
- `Embrace change`: Esperar que los *requerimientos cambien*. *Diseñar* el sistema para *acomodar estos cambios*. 
- `Incremental delivery`: Se hace el diseño en incrementos. Los clientes definen que requerimientos se incluyen en las interaciones.
- `Maintain simplicity`: Mantener la *mayor simplicidad* posible *tanto en el sistema como en el proceso*. Eliminar cuando sea posible complejidad. 
- `People, not process:` Los miembros del equipo deben trabajar *en sus propias formas*, sin ser limitados por un proceso pre-establesido. Se reconocen y se expotan las *habilidades del equipo*. 

#### Donde se utiliza estas metodologias?
Estas metodologias tiene mucho exito en los siguientes casos: 
- Se esta diseñando un *sistema pequeño o mediano porte*. 
- Cuando hay *clientes/representantes claramente interesados en participar* del proyecto. O hay *regulaciones* que te pueden afectar. 

# Tecnicas de desarrolo agil
- Una de los tecnicas mas significativas fue *extreme Programming* (XP)
- La idea de XP era llevar buenas practicas a un nivel extremo. 
- En XP, los requerimientos son *scenarios* o tambien llamados *user story*. Los programadores *trabajan en parejas* y hacen *test-first* (hacer los test antes que la implementacion) y se deben *ejecutar correctamente todos los test* antes de poder integrar el sistema.
- Uno de los mayores problemas de Xp es que no se pudo adaptar a la mayoria de ambientes empresariales
- El mejor aporte de XP fueron las practicas que propuso.

#### Practicas de XP
- `Collective ownership`: Los desarrolares trabajan en todas las areas del sistema. Por lo que es *responsabilidad de todo los desarroladores por el codigo de todo el sistema*. 
- `Continuous integration`: Apenas una tarea es completada, *la misma es integrada en el sistema* si paso todos los test.
- `Incremental planning`: Los requerimientos son recolectados por **story cards**, luego *divididos en tareas* y las mismas *son realizadas en base al tiempo disponible* y prioridad. 
- `On-site cuestomer`: Un *cliente del sistema* tiene que estar *disponible todo el tiempo*, incluso *es parte del equipo de desarrolo* y es el *encargado de traer los requerimientos*. 
- `Pair programming`: Se desarrola en pares
- `Refactoring`: Se espera que *todos los desarroladores* realizen *refactos* a medida que se identifica *un punto de mejora* en el codigo.
- `Simple design`: El diseño esta *unicamente pensado* para los *requerimientos actuales*, para nada mas
- `Small releases`: *Primero se desarrola* (entiendo que en las primeras liberaciones) *el conjunto de funcionalidades que tiene valor de negoci*o. Las liberaciones son frecuentes
- `Sustainable pace` (ridmo sostenible): "*Gran cantidad de horas extras son consideradas inaceptables*. El efecto neto a menudo reduce la calidad del código y a mediano plazo la productividad" 
- `Test first development`: Se utiliza una *heramienta automatizada* para los test. Los *mismos son desarrolados* *antes que se implemente la funcionalidad* . 
 

### Users stories
- No se tiene una actividad de *requierement engineering activity*. El proceso de obtenecion de requerimientos se hace junto con el desarrolo.
- Las *users stories* fueron diseñadas para simplificar esta tarea. 
- Una users storie es un *esenario* de uso donde se descibe lo que el usuario experimienta. 
- Luego el usuario y el equipo de desarrolo discuten el esenario y desarrolan una *story card* que es una *brebe historia de lo que necesita el usuario*. 
- Luego que se haya desarrolado la story card, el equipo la divide en *task* a la cual estima el costo de realizacion. Luego se pueden *refinar esos requerimientos* con el cliente. 
- Es el cliente es quien *determina la prioridad de la user stories* para aportar usabilidad al sistema. 
- Las users stories son mas *comodas* para los clientes que trabajar con documentos de espsificacion de requerimientos
- Algunos problemas de las users stories:
	- Falta de completitud
	- Dificil jusgar si una sola historia brinda toda la informacion necesaria de la funcionalidad

### Refactoring


### Test-first development


