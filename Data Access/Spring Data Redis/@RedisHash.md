#### @RedisHash

The `@RedisHash` annotation marks a class as a Redis hash.

- **Example**:
  ```java
  import org.springframework.data.annotation.Id;
  import org.springframework.data.redis.core.RedisHash;

  @RedisHash("users")
  public class User {
      @Id
      private String id;
      private String name;
      private String email;

      // getters and setters
  }
  ```

