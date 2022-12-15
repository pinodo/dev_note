<!-- HEADER -->
<div align="center">
  <h1 align="center">4. Singleton Pattern</h1>
</div>

# What is Singleton Pattern?
> A design pattern that creates only one instance of class
>
> By using a private constructor, it blocks creating a new instance externally

## Code Example
### class
```java
 public class Singleton {
    // only one instance
    private static final Singleton instance = new SingleTon();
    
    // if an object instance is in demand, it allows to check only by static method
    public static Singleton getInstance() {
        return instance;
    }
    
    // private constructor: blocks creating an instance by new keyword externally
    private Singleton() {}
}
```

### test class

```java
import org.assertj.core.api.Assertions;
import org.junit.jupiter.api.DisplayName;
import org.junit.jupiter.api.Test;

public class SingletonTest {
    
    @Test
    @DisplayName("Object usage, Singleton")
    public void singletonTest() {
        Singleton singletonObj1 = Singleton.getInstance();
        Singleton singletonObj2 = Singleton.getInstance();

        // return true
        Assertions.assertThat(singlton1Obj1).isSameAs(singletonObj2);
    }
}
```

## Limitation
* Lots of code when implementing
* Client depends on the implementation class; DIP rule breaks
* It is hard to test the code
* It is hard to modify or init the inner feature

# Singleton Container
> Singleton container resolves the limitation of a singleton pattern and manages the object instance by singleton
> 
> @Bean is managed as singleton

## Singleton container features
* Spring container manages the object instance as singleton
* Spring container == Singleton container
* Resolves all the <a href="#Limitations">limitation</a> above

## Code Example

### class code

```java
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;

@Configuration
public class AppConfig {
    
    @Bean
    public Service service() {
        return new ServiceImpl(...);
    }
}
```
```java
public class ServiceImpl implements Service {
    ...
}
```
### test code
```java
import org.junit.jupiter.api.DisplayName;
import org.junit.jupiter.api.Test;
import yourservicepackage;

public class SpringSingletonTest {
    
    @Test
    @DisplayName("Spring container and singleton")
    void springContainer() {
        ApplicationContext ac = new AnnotationConfigApplicationContext(AppConfig.class);

        Service service1 = ac.getBean("service", Service.class);
        Service service2 = ac.getBean("service", Service.class);

        // return true
        assertThat(service1).isSameAs(service2);
    }
}
```

## Advantage
* Whenever the customer requests, the program shares the pre-made object and reuse

## Precautious
> Since multiple clients share one instance, singleton object must be structured stateless
> 
> * No dependency field in a client
> * No variable field that a client can modify
> * Should use local variable, parameter, ThreadLocal, etc,. instead of field

