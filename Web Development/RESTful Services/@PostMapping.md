#### @PostMapping

The `@PostMapping` annotation is a specialized version of `@RequestMapping` for HTTP POST requests. It's used to map POST requests onto specific handler methods.

- Example:
  ```java
  import org.springframework.web.bind.annotation.PostMapping;
  import org.springframework.web.bind.annotation.RequestBody;
  import org.springframework.web.bind.annotation.RestController;

  @RestController
  public class UserController {

      @PostMapping("/users")
      public User createUser(@RequestBody User user) {
          return userService.save(user);
      }
  }
  ```
