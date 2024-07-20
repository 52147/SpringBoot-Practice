#### Type-safe Configuration

1. **@ConfigurationProperties**:
   - Used to bind properties to POJOs (Plain Old Java Objects) in a type-safe manner.
   - Example:
     ```java
     @ConfigurationProperties(prefix = "server")
     public class ServerProperties {
       private int port;
       // getters and setters
     }
     ```

2. **Binding to POJOs**:
   - Example:
     ```yaml
     server:
       port: 8084
     ```
     ```java
     @ConfigurationProperties(prefix = "server")
     public class ServerConfig {
       private int port;
       // getters and setters
     }
     ```
