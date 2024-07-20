### Custom Server Configuration

You can customize the embedded server configuration to meet specific requirements, such as setting the port, context path, or other server-specific properties.

- **Port and Context Path**:
  - Example in `application.properties`:
    ```properties
    server.port=9000
    server.servlet.context-path=/myapp
    ```

- **Programmatically Setting Server Properties**:
  - Example with `ConfigurableServletWebServerFactory`:
    ```java
    import org.springframework.boot.web.server.ConfigurableServletWebServerFactory;
    import org.springframework.context.annotation.Bean;
    import org.springframework.context.annotation.Configuration;

    @Configuration
    public class ServerConfig {

        @Bean
        public ConfigurableServletWebServerFactory webServerFactory() {
            ConfigurableServletWebServerFactory factory = new TomcatServletWebServerFactory();
            factory.setPort(9000);
            factory.setContextPath("/myapp");
            return factory;
        }
    }
    ```

### Summary

- **Tomcat** is the default embedded server in Spring Boot, but you can switch to **Jetty** or **Undertow** by adding the appropriate dependencies.
- Custom server configuration can be done via `application.properties` or by defining configuration beans.
- Embedded servers simplify deployment and are suitable for microservices and other standalone web applications.

