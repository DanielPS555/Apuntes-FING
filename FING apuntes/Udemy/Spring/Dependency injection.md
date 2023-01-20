La idea principal es continuar con el principio de *Inversion of Control*, donde ahora a quien le delegamos la responsabilidad de crear el objeto y mantenerlo, tambien sera quien se encarga de pasarle las dependencias.  

Hay dos tipos de inyecciones: 
- Inyeciones por constructor
- Inyeciones por setter


## Ejemplo de inyecion de dependencia por constructor

Supongamos que tenemos una clase `BaseballCoach` que requiere de la interface `FortuneService` implementada en `HappyFortuneService` .

Para ello se crea el siguiente been. 

```xml
<bean id="myFortuneService"  
      class="springdemo.HappyFortuneService">  
</bean>
```

Luego se importa por constructor en la clase 

```java
public BaseballCoach(FortuneService fortuneService){  
    this.fortuneService = fortuneService;  
}
```

Luego la configuracion en el xml es asi 
```xml
<bean id="myCoach"  
   class="springdemo.BaseballCoach">   
   <constructor-arg ref="myFortuneService" />  
</bean>
```


## Inyecion de dependencia por setter

La forma para hacer una inyecion de dependencia via un setter, es tener un setter de una propiedad bajo el siguiente formato: 

Si la propiedad es `propiedadA`, entonces el setter debe llamarse `setPropiedadA`. 

Luego a nivel de xml se ve asi: 

```xml
<bean id="interfaceName" class="claseName">   
   <property name="propiedadA" ref="propiedadABeenName" />
</bean>
```

## Inyectar valores literales 
Para ello remplazamos el valor de `ref` de la etiqueta `property` por `value`

```xml
<bean id="interfaceName" class="claseName">   
   <property name="propiedadA" value="valorDeLaPropiedadA" />
</bean>
```

## Inyectar valores de un archivo de configuracion
Lo primero que se requiere en es archivo con las propiedades, para ello podemos crear por ejemplo `sport.properties` con la siguiente informacion:

```
foo.email=superEmail.com
foo.team=algun super team
```

Para cargar un archivo de configuracion se hace añade al archivo de configuracion de Spring la siguiente linea: 

```xml
<context:property-placeholder Location="classpath:sport.properties"/>
```

Luego podemos llamar al valor de esta forma: 
```xml
<bean id="Coach" class="SuperCoach">   
   <property name="email" value="${foo.email}" />
   <property name="team" value="${foo.team}" />
</bean>
```
