#### @Document

The `@Document` annotation marks a class as a MongoDB document.

- **Example**:
  ```java
  import org.springframework.data.annotation.Id;
  import org.springframework.data.mongodb.core.mapping.Document;

  @Document(collection = "users")
  public class User {
      @Id
      private String id;
      private String name;
      private String email;

      // getters and setters
  }
  ```

