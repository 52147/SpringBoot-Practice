### Core Concepts of Spring Framework and Spring Boot

#### Spring Framework

**Dependency Injection**
- **`@Autowired`**: Used to inject a bean automatically by matching the data type. It can be used on fields, constructors, or methods.
- **Singleton Scope**: The default scope of a bean where a single instance of a bean is created and shared across the entire Spring container.

**Aspect-Oriented Programming (AOP)**
- Provides the ability to add behavior to existing code without modifying the code itself. Commonly used for cross-cutting concerns like logging, transaction management, and security.

#### Spring Boot

**Auto-Configuration**
- **Conditional Beans**: Beans that are only created when certain conditions are met, using annotations like `@ConditionalOnProperty`, `@ConditionalOnMissingBean`, etc.
- **`@SpringBootApplication`**: A convenience annotation that combines `@Configuration`, `@EnableAutoConfiguration`, and `@ComponentScan` with their default attributes. It's used to mark the main class of a Spring Boot application and enable auto-configuration.
  - **Excluding Auto-Configuration Classes**: To exclude specific auto-configuration classes, use `@SpringBootApplication(exclude = {ClassName.class})`.
- **`@EnableAutoConfiguration`**: Enables auto-configuration in Spring Boot applications. It attempts to automatically configure your Spring application based on the jar dependencies you have added.

**Starter POMs**
- **`spring-boot-starter-web`**: Used to create web applications, including RESTful applications using Spring MVC.
- **`spring-boot-starter-data-jpa`**: Used to include Spring Data JPA in your project, which makes it easier to implement JPA-based repositories.

**Spring Boot CLI**
- A command-line tool that helps in building Spring Boot applications quickly using Groovy-based scripting.
- Useful for rapid prototyping.

**Running a Spring Boot Application**
- **Using `java -jar` Command**: Package your application into a jar file and run it using `java -jar your-application.jar`.
- **Using an IDE (e.g., IntelliJ IDEA, Eclipse)**: Most IDEs support running Spring Boot applications directly from the IDE.
- **Using `mvn spring-boot:run`**: Run your application using the Maven Spring Boot plugin.

These core concepts provide a foundational understanding of how to work with the Spring Framework and Spring Boot, enabling you to develop robust and scalable Java applications efficiently.