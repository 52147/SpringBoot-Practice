### Embedded Servers in Spring Boot

Spring Boot comes with embedded servers, making it easy to run web applications without needing to deploy them to an external application server. The three primary embedded servers supported by Spring Boot are Tomcat, Jetty, and Undertow.

#### 1. Tomcat

Tomcat is the default embedded servlet container used by Spring Boot. It provides a lightweight, fast, and powerful way to run web applications.

- **Default Configuration**:
  - Spring Boot automatically includes Tomcat as the default embedded server.
  - Example of running a Spring Boot application with the default Tomcat:
    ```java
    @SpringBootApplication
    public class Application {
        public static void main(String[] args) {
            SpringApplication.run(Application.class, args);
        }
    }
    ```

- **Custom Configuration**:
  - You can customize the Tomcat server settings in `application.properties` or by creating a `TomcatServletWebServerFactory` bean.
  - Example in `application.properties`:
    ```properties
    server.port=8081
    server.tomcat.max-threads=200
    ```

  - Example with a `TomcatServletWebServerFactory` bean:
    ```java
    import org.springframework.boot.web.embedded.tomcat.TomcatServletWebServerFactory;
    import org.springframework.context.annotation.Bean;
    import org.springframework.context.annotation.Configuration;

    @Configuration
    public class TomcatConfig {

        @Bean
        public TomcatServletWebServerFactory tomcatFactory() {
            TomcatServletWebServerFactory factory = new TomcatServletWebServerFactory();
            factory.setPort(8081);
            factory.setContextPath("/app");
            return factory;
        }
    }
    ```
