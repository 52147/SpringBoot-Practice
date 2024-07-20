### Configuration in Spring Boot

Spring Boot applications can be configured in various ways to suit different environments and use cases. Below is an overview of the main configuration options available in Spring Boot:

#### YAML/Properties Files

1. **application.yml**:
   - A YAML file for configuring properties.
   - Example:
     ```yaml
     server:
       port: 8080
     ```

2. **application.properties**:
   - A properties file for configuring properties.
   - Example:
     ```properties
     server.port=8080
     ```

#### Injecting Values from Properties Files

1. **@Value**:
   - Used to inject values from properties files into Spring beans.
   - Example:
     ```java
     @Value("${server.port}")
     private int serverPort;
     ```
