#### ResponseEntity

The `ResponseEntity` class represents the whole HTTP response, including the status code, headers, and body. It can be used to configure the HTTP response in detail.

- Example:
  ```java
  import org.springframework.http.HttpStatus;
  import org.springframework.http.ResponseEntity;
  import org.springframework.web.bind.annotation.GetMapping;
  import org.springframework.web.bind.annotation.PathVariable;
  import org.springframework.web.bind.annotation.RestController;

  @RestController
  public class UserController {

      @GetMapping("/users/{id}")
      public ResponseEntity<User> getUserById(@PathVariable Long id) {
          User user = userService.findById(id);
          if (user == null) {
              return new ResponseEntity<>(HttpStatus.NOT_FOUND);
          }
          return new ResponseEntity<>(user, HttpStatus.OK);
      }
  }
  ```

### Complete Example

Below is a complete example of a Spring Boot application that creates RESTful web services.

1. **User.java** (Model):
   ```java
   public class User {
       private Long id;
       private String name;
       private String email;

       // getters and setters
   }
   ```

2. **UserService.java** (Service):
   ```java
   import java.util.ArrayList;
   import java.util.List;

   public class UserService {
       private List<User> users = new ArrayList<>();

       public List<User> findAll() {
           return users;
       }

       public User findById(Long id) {
           return users.stream().filter(user -> user.getId().equals(id)).findFirst().orElse(null);
       }

       public User save(User user) {
           users.add(user);
           return user;
       }
   }
   ```

3. **UserController.java** (Controller):
   ```java
   import org.springframework.beans.factory.annotation.Autowired;
   import org.springframework.http.HttpStatus;
   import org.springframework.http.ResponseEntity;
   import org.springframework.web.bind.annotation.*;

   import java.util.List;

   @RestController
   @RequestMapping("/api")
   public class UserController {

       @Autowired
       private UserService userService;

       @GetMapping("/users")
       public List<User> getAllUsers() {
           return userService.findAll();
       }

       @GetMapping("/users/{id}")
       public ResponseEntity<User> getUserById(@PathVariable Long id) {
           User user = userService.findById(id);
           if (user == null) {
               return new ResponseEntity<>(HttpStatus.NOT_FOUND);
           }
           return new ResponseEntity<>(user, HttpStatus.OK);
       }

       @PostMapping("/users")
       public ResponseEntity<User> createUser(@RequestBody User user) {
           User createdUser = userService.save(user);
           return new ResponseEntity<>(createdUser, HttpStatus.CREATED);
       }
   }
   ```

### Summary

- `@RestController` is used to create a controller that returns JSON/XML responses.
- `@GetMapping` and `@PostMapping` are specialized annotations for mapping GET and POST requests to handler methods.
- `ResponseEntity` is used to configure the HTTP response in detail, including status code, headers, and body.
- Creating RESTful APIs involves defining models, services, and controllers that handle HTTP requests and return appropriate responses.

This setup provides a comprehensive framework for developing RESTful web services in Spring Boot.

