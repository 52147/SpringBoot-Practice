#### JpaRepository

The `JpaRepository` interface extends `CrudRepository` and `PagingAndSortingRepository`. It provides JPA-specific methods such as flushing the persistence context and deleting records in a batch.

- **Example**:
  ```java
  import org.springframework.data.jpa.repository.JpaRepository;

  public interface UserRepository extends JpaRepository<User, Long> {
  }
  ```
