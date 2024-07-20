#### Profiles

1. **@Profile**:
   - Used to specify that a bean is only created when a specific profile is active.
   - Example:
     ```java
     @Service
     @Profile("dev")
     public class DevService {
       // ...
     }
     ```

2. **application-{profile}.yml**:
   - YAML file specific to a profile.
   - Example: `application-dev.yml`
     ```yaml
     server:
       port: 8081
     ```

