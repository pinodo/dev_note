<!-- HEADER -->
<div align="center">
  <h1 align="center">3. IoC, DI, Container</h1>
</div>

# IoC
> IoC (Inversion of Control)
> 
> Previous Program: Client implement object creates, connects, and executes the server implement object
> 
> **Limitation**: Whenever the business logic changes, developers should lookup system and modify the name or logic one by one
> 
> **Solution**: By making the AppConfig file, which controls the flow of the program, we can externally control the flow

# DI
> DI (Dependency Injection)
> 
> Dependency: Static / Variable object(Instance)
> 
> * Static Dependency
>   * We can analyze the dependencies by looking up the import statement
>   * **Limitation**: We can't define what object is injected to the implementation class
> * Variable Object Dependency
>   * Upon a runtime, the program creates the object externally, and pass them to client to connect with the server
>   * It creates the object instance and passes the reference
>   * **Advantages**: We can switch implementation class by not modifying the static classes' dependencies

# DI Container
> DI Container manages the objects and dependencies and connects the dependencies