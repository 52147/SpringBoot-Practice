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