**Dependency Injection**
- **`@Autowired`**: Used to inject a bean automatically by matching the data type. It can be used on fields, constructors, or methods.
- **Singleton Scope**: The default scope of a bean where a single instance of a bean is created and shared across the entire Spring container.

### Dependency Injection (DI)

**Dependency Injection** is a design pattern used to implement Inversion of Control (IoC), where the control of creating and managing objects is transferred from the class itself to an external entity (typically a framework or container). In the context of the Spring Framework, DI is a fundamental concept that helps in building loosely coupled and easily testable applications.

#### Key Concepts of Dependency Injection

1. **Inversion of Control (IoC)**
   - The principle of transferring control from the application to the Spring IoC container, which manages the creation and lifecycle of beans.

2. **Beans**
   - Objects that form the backbone of a Spring application and are managed by the Spring IoC container. A bean is an object that is instantiated, assembled, and otherwise managed by a Spring container.

3. **Types of Dependency Injection**
   - **Constructor Injection**: Dependencies are provided through the class constructor.
   - **Setter Injection**: Dependencies are provided through setter methods.
   - **Field Injection**: Dependencies are injected directly into fields (usually via reflection).

#### How Dependency Injection Works in Spring

**1. Constructor Injection**

Constructor injection is performed by passing the required dependencies through a class constructor. This method ensures that the dependency is provided at the time of object creation.

```java
@Component
public class MyService {

    private final MyRepository myRepository;

    @Autowired
    public MyService(MyRepository myRepository) {
        this.myRepository = myRepository;
    }

    // Methods and logic
}
```

**2. Setter Injection**

Setter injection uses setter methods to inject dependencies into a bean. It is more flexible than constructor injection and allows dependencies to be changed or added after the object is created.

```java
@Component
public class MyService {

    private MyRepository myRepository;

    @Autowired
    public void setMyRepository(MyRepository myRepository) {
        this.myRepository = myRepository;
    }

    // Methods and logic
}
```

**3. Field Injection**

Field injection uses annotations directly on fields to inject dependencies. While it's the simplest form of injection, it is less preferred because it uses reflection and makes the class harder to test.

```java
@Component
public class MyService {

    @Autowired
    private MyRepository myRepository;

    // Methods and logic
}
```

#### Benefits of Dependency Injection

1. **Loose Coupling**
   - By injecting dependencies, classes are not tightly bound to their dependencies, making them more flexible and easier to maintain.

2. **Enhanced Testability**
   - Classes can be easily tested by injecting mock dependencies, which simplifies unit testing.

3. **Improved Code Readability and Maintenance**
   - Dependency injection makes the structure of the application clearer and the configuration of dependencies explicit.

4. **Easier Configuration Management**
   - Spring allows external configuration of dependencies using XML or Java-based configuration, facilitating easier changes and management.

#### Spring IoC Container

The IoC container is responsible for instantiating, configuring, and assembling the beans. The container receives instructions on what objects to instantiate, configure, and assemble by reading configuration metadata.

- **ApplicationContext**: The primary interface for accessing the Spring IoC container.
- **BeanFactory**: A more basic container that provides the fundamental DI capabilities.

Example configuration using Java-based configuration:

```java
@Configuration
public class AppConfig {

    @Bean
    public MyRepository myRepository() {
        return new MyRepositoryImpl();
    }

    @Bean
    public MyService myService() {
        return new MyService(myRepository());
    }
}
```

In this example, the `AppConfig` class defines two beans, `myRepository` and `myService`, and the Spring IoC container manages their lifecycle and dependencies.

Dependency Injection is a powerful pattern that enhances the flexibility, maintainability, and testability of applications by promoting loose coupling and clear separation of concerns.

