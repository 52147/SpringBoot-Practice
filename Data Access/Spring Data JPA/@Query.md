#### @Query

The `@Query` annotation is used to define custom queries using JPQL (Java Persistence Query Language) or native SQL.

- **Example**:
  ```java
  import org.springframework.data.jpa.repository.Query;
  import org.springframework.data.repository.query.Param;
  import java.util.List;

  public interface UserRepository extends JpaRepository<User, Long> {
      
      @Query("SELECT u FROM User u WHERE u.name = :name")
      List<User> findByName(@Param("name") String name);
  }
  ```
