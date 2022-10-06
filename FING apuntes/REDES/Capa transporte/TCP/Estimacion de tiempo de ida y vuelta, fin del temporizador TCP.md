# Estimacion de tiempo de ida y vuelta, fin del temporizador TCP 

Como TCP tiene sistemas para controlar la perdida de paquetes, uno de los problemas mas grandes es estimar el tiempo que se le tiene que establecer a dicho timer. Ya que si es muy corto se va a enviar un segmento al pedo (y aumenta la congestion de la red), y si es muy largo se pierde tiempo valioso en enviar el segmento.

TCP toma una muestra del RTT a la cada vez (no en simultanio), el cual se lo llama *RTTMuestra*, osea que para cada instante de tiempo, se esta midiendo el tiempo de uno solo de los segmentos enviados pero aun no reconocidos. *Por lo tanto tenemos un RTTMuestra cada RTT segundos*.

Para calcular el *RTTEstimativo* utilizamos una funcion de la forma *media movil exponencialmente ponderada* tiene la siguiente forma:

$RTTEstimativo = (1 - \alpha).RTTEstimativo + \alpha.RTTMuestra$  con $\alpha = 0.125$.

Tambien calculamos que tanto la variabilidad (*DTTDesv*) del RTTMuestra con el RTTEstimado como 

$RTTDesv = (1 - \beta).RTTDesv + \beta.|RTTMuestra - RTTEstimativo|$ con $\beta = 0.250$ 

El tiempo para el temporizador TCP sera:

$IntervaloFinTemporizador = RTTEstimativo + 4.RTTDesv$ 

*Por defecto se sea en un 1s al comenzar*, luego se va calculado, *Si se vence el temporizador, se duplica el anterior* tiempo, y asi se continua, cuando salimos de ese modo de duplicar el tiempo recivimos respuesta, volvemos a calcular el tiempo como esta dicho aqui. 
