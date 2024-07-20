#### @Field

The `@Field` annotation is used to map a field in a document to a field in the class.

- **Example**:
  ```java
  import org.springframework.data.mongodb.core.mapping.Field;

  @Document(collection = "users")
  public class User {
      @Id
      private String id;

      @Field("user_name")
      private String name;

      private String email;

      // getters and setters
  }
  ```
