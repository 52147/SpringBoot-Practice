#### CrudRepository

The `CrudRepository` interface provides CRUD (Create, Read, Update, Delete) operations.

- **Example**:
  ```java
  import org.springframework.data.repository.CrudRepository;

  public interface UserRepository extends CrudRepository<User, Long> {
  }
  ```
