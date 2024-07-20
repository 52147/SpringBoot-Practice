#### 2. Jetty

Jetty is another popular embedded server supported by Spring Boot. It is known for its performance and scalability.

- **Adding Jetty Dependency**:
  - To use Jetty instead of Tomcat, you need to exclude Tomcat and include Jetty in your `pom.xml` or `build.gradle`.
  - Example for `pom.xml`:
    ```xml
    <dependencies>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-web</artifactId>
            <exclusions>
                <exclusion>
                    <groupId>org.springframework.boot</groupId>
                    <artifactId>spring-boot-starter-tomcat</artifactId>
                </exclusion>
            </exclusions>
        </dependency>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-jetty</artifactId>
        </dependency>
    </dependencies>
    ```

- **Custom Configuration**:
  - You can customize the Jetty server settings in `application.properties` or by creating a `JettyServletWebServerFactory` bean.
  - Example in `application.properties`:
    ```properties
    server.port=8082
    ```

  - Example with a `JettyServletWebServerFactory` bean:
    ```java
    import org.springframework.boot.web.embedded.jetty.JettyServletWebServerFactory;
    import org.springframework.context.annotation.Bean;
    import org.springframework.context.annotation.Configuration;

    @Configuration
    public class JettyConfig {

        @Bean
        public JettyServletWebServerFactory jettyFactory() {
            JettyServletWebServerFactory factory = new JettyServletWebServerFactory();
            factory.setPort(8082);
            return factory;
        }
    }
    ```
