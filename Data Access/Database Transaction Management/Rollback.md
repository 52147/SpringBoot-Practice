#### Rollback

The `@Transactional` annotation can also define rollback behavior. By default, transactions will rollback on unchecked exceptions, but you can specify exceptions to trigger a rollback.

- **Example**:
  ```java
  @Transactional(rollbackFor = Exception.class)
  public void saveAndRollbackOnError(User user) throws Exception {
      userRepository.save(user);
      if (someCondition) {
          throw new Exception("Trigger rollback");
      }
  }
  ```

  ### Complete Example with Database Transaction Management

1. **User.java** (Model):
   ```java
   import javax.persistence.Entity;
   import javax.persistence.Id;

   @Entity
   public class User {
       @Id
       private Long id;
       private String name;
       private String email;

       // getters and setters
   }
   ```

2. **UserRepository.java** (Repository):
   ```java
   import org.springframework.data.jpa.repository.JpaRepository;

   public interface UserRepository extends JpaRepository<User, Long> {
   }
   ```

3. **UserService.java** (Service with Transaction Management):
   ```java
   import org.springframework.beans.factory.annotation.Autowired;
   import org.springframework.stereotype.Service;
   import org.springframework.transaction.annotation.Propagation;
   import org.springframework.transaction.annotation.Transactional;

   @Service
   public class UserService {

       @Autowired
       private UserRepository userRepository;

       @Transactional
       public void saveUser(User user) {
           userRepository.save(user);
       }

       @Transactional(propagation = Propagation.REQUIRES_NEW)
       public void saveWithNewTransaction(User user) {
           userRepository.save(user);
       }

       @Transactional(isolation = Isolation.SERIALIZABLE)
       public void performSerializableTransaction(User user) {
           userRepository.save(user);
       }

       @Transactional(rollbackFor = Exception.class)
       public void saveAndRollbackOnError(User user) throws Exception {
           userRepository.save(user);
           if (someCondition()) {
               throw new Exception("Trigger rollback");
           }
       }

       private boolean someCondition() {
           // Dummy condition for example
           return true;
       }
   }
   ```

### Summary

- **@Transactional**: Used to define transactional boundaries.
- **Propagation**: Defines how transactions relate to each other.
- **Isolation**: Defines the level of visibility a transaction has to other concurrent transactions.
- **Rollback**: Defines rollback behavior for transactions.

Using `@Transactional` in Spring helps manage database transactions efficiently, ensuring data integrity and consistency across operations.


