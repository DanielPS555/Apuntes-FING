En resumen eso de lo que trata es que la contruccion y manejo de determinados objetos sera externalizado, en particular sera manejado por una *Fabrica*. 

Estos objetos devueltos por lo spring containers se llaman Spring Bean. 

> A "Spring Bean" is simply a Java object.
	When Java objects are created by the Spring Container, then Spring refers to them as "Spring Beans".
	Spring Beans are created from normal Java classes .... just like Java objects.


## Ejemplo 

En este ejemplo tenemos una interface llama `Coach`

```java
public interface Coach {   
    String whatToDo();  
}
```

Y dos implementacion de esta interface, el FootBallCoach y el BaseBallCoach

```java
public class BaseballCoach implements Coach{  
  
    @Override  
    public String whatToDo() {  
        return "Do some baseball";  
    }  
}
```

```java
public class FootballCoach implements Coach{  
  
    @Override  
    public String whatToDo() {  
        return "i don't no, do something which is relate to football ";  
    }  
}
```

Luego una clase llama `HelloSpringApp`, la cual sera quien consuma estas clases, para obtener una instancia del Coach, eligiendo la implementacion usamos el Spring containers, en este caso en particular la configuracion xml, por medio de un archivo de configuracion llamado `applicationContext.xml` .

```xml
<?xml version="1.0" encoding="UTF-8"?>  
<beans xmlns="http://www.springframework.org/schema/beans"  
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"   
xmlns:context="http://www.springframework.org/schema/context"  
    xsi:schemaLocation="http://www.springframework.org/schema/beans  
    http://www.springframework.org/schema/beans/spring-beans.xsd    http://www.springframework.org/schema/context    http://www.springframework.org/schema/context/spring-context.xsd">  
  
    <!-- Define your beans here -->  
    <bean id="myCoach"  
        class="springDemo.BaseballCoach">  
    </bean>  
  
</beans>
```

Luego para obtener en Spring been y consumirlo se hace en el siguiente ejemplo 

```java 
import org.springframework.context.support.ClassPathXmlApplicationContext;  
  
public class HelloSpringApp {  
  
    public static void main(String[] args){  
  
        //Creo el contexto, utilizado el archivo de configuracion  
        ClassPathXmlApplicationContext context = new ClassPathXmlApplicationContext("applicationContext.xml");  
  
        //Obtengo el been apropiado  
        Coach c = context.getBean("myCoach", Coach.class);  
  
        //Llamo al metodo que quiero del been  
        System.out.println(c.whatToDo());  
  
        //Cierro el contexto  
        context.close();  
  
    }  
}
```


**Importante:** Notar que en el metodo getBean le pasamos el tipo de interface, con eso ganamos que es Spring quien hace el cast, ademas el cast lo hace de forma segura, tirado BeanNotOfRequiredTypeException en caso de fallar. Una explicacion mas detallada: 

> Behaves the same as getBean(String), but provides a measure of type safety by throwing a BeanNotOfRequiredTypeException if the bean is not of the required type. This means that ClassCastException can't be thrown on casting the result correctly, as can happen with getBean(String).

