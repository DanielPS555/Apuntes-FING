El `Bean scope` de un Been se refiere al ciclo de vida (`Lifecycle`) del bean. Respondiendo a las siguientes preguntas: 
- Cuanto va a vivir un been 
- Cuantas instancias se pueden crear de un been 
- Como el been es compartido

Por defecto el scope es `Singleton`.  Usa solo crean una instancia y es compartida por todo. 


Para espesificar el scope de un been se hace añadiendo el atributo `scope` en la etiqueta `Bean`

Por ejemplo 

```xml
<beans>
	<bean id="myCoach"
		class="TrackCoach"	
		scope="singleton">
		...
	</bean>
</beans>
```


## Algunos Bean Scopes habilitados en Spring

- `Singleton`: Una unica instancia por bean. Es la opcion por defecto
- `Prototype`: Una instancia por cada vez que se la solicita 

*Las siguientes tres son de uso excluisvo de la web*

- `Request`:  Es un scope por cada Http web request
- `session`: Es un scope por cada Http session
- `global-session`: Es un scope por cada session global http


## Bean lifecycle methods y hooks

Se pueden añadir `bean initialization` y `bean destruction` a los ciclos de vida de los been. 
Un ejemplo claro de inicializador podria ser reservar algunos recursos para un servicio, etc. 

Se le llama `Hooks` al codigo que es llamado por spring durante su Life cycle

La forma de configurar esos hooks es la siguiente: 

- Para añadir un inicialziador se le agrega un atributo al been con la etiqueta: `init-method = "nombre del metodo de inicio"`
- Para añadir un destructor es analogo pero con la etiqueta `destroy-method`

Ninguno de los metodos que se hagan referencia en los hooks pueden tener argumentos

*Importante:* En un bean con scope Prototype no se llama al destructor hook, es por eso que se debe implementar la interface `DisposableBean` en esos casos, re implementado el metodo `destroy`. 