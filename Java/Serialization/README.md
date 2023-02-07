<!-- HEADER -->
<div align="center">
  <h1 align="center">Serialization</h1>
</div>

```shell
public interface Serializable {
}
```

# When to use?
* When you save the created object as a file
* When you read the saved object
* When you receive the object from the other server
> Implementing Serializable interface enables the object to save or to transport to the other server in JVM

# What is Serialization?
> Object serialization is that an object can be represented as a sequence of bytes that includes the object's data as
> well as information about the object's type and the types of data stored in the object
> 
> ObjectInputStream and ObjectOutputStream classes are high-level streams that contain the methods for serializing and
> deserializing an object
```java
Example

public class Employee implements java.io.Serializable {
  public String name;
  public String address;
  public transient int SSN; // if a field is not serializable, it must be marked transient
  public int number;
}
```