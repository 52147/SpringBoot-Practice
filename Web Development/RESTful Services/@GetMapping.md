#### @GetMapping

The `@GetMapping` annotation is a specialized version of `@RequestMapping` for HTTP GET requests. It's used to map GET requests onto specific handler methods.

- Example:
  ```java
  import org.springframework.web.bind.annotation.GetMapping;
  import org.springframework.web.bind.annotation.RestController;

  @RestController
  public class UserController {

      @GetMapping("/users")
      public List<User> getAllUsers() {
          return userService.findAll();
      }
  }
  ```
