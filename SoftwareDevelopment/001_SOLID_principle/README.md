<!-- HEADER -->
<div align="center">
  <h1 align="center">1. SOLID principle</h1>
</div>

# Why we use design patterns?
> Universal standards
>
> Higher level of reuse - clarifies class responsibilities

## 1. SRP (Single Responsibility Principle)
* One class has one responsibiity 
* Using Abstraction or Implementation, subclass has their own responsibility

## 2. OCP (Open-Closed Principle)
* Objects or entities should be open for extension but closed for modification
* Polymorphism
* Make an interface class, then implements
  > OrderService.java (interface) -> OrderServiceImpl.java (implemented class)

## 3. LSP (Liskov Substitution Principle)
* Subclass should obey the all rule of interface
  ```shell
  (OrderService.java) - Interface
  Order order(Long custId, String name, int price);
  
  (OrderServiceImpl.java) - Implemented class
  @Override
  public Order order(Long custId, String name, int price) {
  "matches the return value, parameters of interface's ones"
    Customer c = ...
    ...
    return new Order(custId, name, price);
  }
  ```
  
## 4. ISP (Interface Segregation Principle)
* It is much better to use multiple interfaces rather than an universal interface

## 5. DIP (Dependency Inversion Principle)
* Entities must depend on abstractions, not on concretions
* The high-level module must not depend on the low-level module