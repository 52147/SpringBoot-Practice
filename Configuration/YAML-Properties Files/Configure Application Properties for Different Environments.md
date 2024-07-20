### Configure Application Properties for Different Environments

Spring Boot supports environment-specific configurations, allowing you to define different property files for different environments.

1. **application.properties**:
   - Default properties file.
   - Example:
     ```properties
     spring.application.name=myapp
     ```

2. **application-{profile}.properties**:
   - Properties file specific to a profile.
   - Example: `application-dev.properties`
     ```properties
     server.port=8086
     ```

3. **application-{profile}.yml**:
   - YAML file specific to a profile.
   - Example: `application-prod.yml`
     ```yaml
     server:
       port: 8087
     ```

### Usage Example

1. **application.properties**:
   ```properties
   spring.application.name=myapp
   ```

2. **application-dev.properties**:
   ```properties
   server.port=8081
   ```

3. **application-prod.yml**:
   ```yaml
   server:
     port: 8082
   ```

In your Spring Boot application, you can activate a profile by setting the `spring.profiles.active` property.

- Command-line:
  ```shell
  java -jar myapp.jar --spring.profiles.active=dev
  ```

- Environment variable:
  ```shell
  export SPRING_PROFILES_ACTIVE=prod
  ```

This configuration allows you to manage different environments (e.g., development, production) efficiently by separating the properties specific to each environment.

