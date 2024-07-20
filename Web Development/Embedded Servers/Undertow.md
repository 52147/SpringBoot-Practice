#### 3. Undertow

Undertow is a lightweight and highly performant web server, also supported by Spring Boot.

- **Adding Undertow Dependency**:
  - To use Undertow instead of Tomcat, you need to exclude Tomcat and include Undertow in your `pom.xml` or `build.gradle`.
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
            <artifactId>spring-boot-starter-undertow</artifactId>
        </dependency>
    </dependencies>
    ```

- **Custom Configuration**:
  - You can customize the Undertow server settings in `application.properties` or by creating an `UndertowServletWebServerFactory` bean.
  - Example in `application.properties`:
    ```properties
    server.port=8083
    ```

  - Example with an `UndertowServletWebServerFactory` bean:
    ```java
    import org.springframework.boot.web.embedded.undertow.UndertowServletWebServerFactory;
    import org.springframework.context.annotation.Bean;
    import org.springframework.context.annotation.Configuration;

    @Configuration
    public class UndertowConfig {

        @Bean
        public UndertowServletWebServerFactory undertowFactory() {
            UndertowServletWebServerFactory factory = new UndertowServletWebServerFactory();
            factory.setPort(8083);
            return factory;
        }
    }
    ```

