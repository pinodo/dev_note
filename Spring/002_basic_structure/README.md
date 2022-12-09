<!-- HEADER -->
<div align="center">
  <h1 align="center">2. Spring Structure & Features</h1>
</div>

# Project Layer
```shell
Controller --> Service --> Repo --> Database
    \             |         /
     \            V        /
      >        Domain     <
      
Service: Implements the core business logic
Repo: Accesses to DB, Manage and store a domain object to DB
Domain: Business domain object ex) customer, order, coupon
```

# Project Structure by Layer
```
com
└── packagename
    └── projectname
        ├── Application.java
        ├── models(domain)
        │   ├── User.java
        │   └── Order.java
        ├── controllers
        │   ├── UserController.java
        │   └── OrderController.java
        ├── services
        │   ├── UserService.java
        │   └── OrderService.java
        ├── repositories
        │   ├── UserRepository.java
        │   └── OrderRepository.java 
        ├── AppConfig
        └── AppUtil
```

# Features
> **Main tech**: Spring DI container / AOP / Event / etc.
> 
> **Web tech**: MVC / WebFlux
> 
> Spring Boot supports the user to easily utilize Spring