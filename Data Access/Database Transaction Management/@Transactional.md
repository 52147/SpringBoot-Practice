### Database Transaction Management

Database transaction management is crucial for ensuring data integrity and consistency. In Spring, the `@Transactional` annotation is used to manage transactions declaratively. Here’s an overview of the key concepts and how `@Transactional` is used in Spring applications.

#### Key Concepts

1. **@Transactional**
2. **Propagation**
3. **Isolation**
4. **Rollback**

#### @Transactional

The `@Transactional` annotation is used to demarcate transactional boundaries. When applied to a method or class, it indicates that the method or all methods within the class should be executed within a transactional context.

- **Example**:
  ```java
  import org.springframework.transaction.annotation.Transactional;
  import org.springframework.beans.factory.annotation.Autowired;
  import org.springframework.stereotype.Service;

  @Service
  public class UserService {

      @Autowired
      private UserRepository userRepository;

      @Transactional
      public void saveUserAndUpdateEmail(User user, String newEmail) {
          userRepository.save(user);
          user.setEmail(newEmail);
          userRepository.save(user);
      }
  }
  ```

