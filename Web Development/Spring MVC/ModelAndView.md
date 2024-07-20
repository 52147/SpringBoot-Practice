#### ModelAndView

The `ModelAndView` class is used to return both the model and the view from a handler method. It holds the model data and the name of the view to be rendered.

- Example:
  ```java
  import org.springframework.web.bind.annotation.RequestMapping;
  import org.springframework.web.bind.annotation.RequestMethod;
  import org.springframework.web.servlet.ModelAndView;

  @Controller
  public class HomeController {

      @RequestMapping(value = "/greeting", method = RequestMethod.GET)
      public ModelAndView greeting() {
          ModelAndView mav = new ModelAndView("greeting"); // view name
          mav.addObject("message", "Hello, World!"); // adding model data
          return mav;
      }
  }
  ```

### Complete Example

Below is a complete example demonstrating how to use `@Controller`, `@RequestMapping`, and `ModelAndView` in a Spring MVC application.

1. **HomeController.java**:
   ```java
   import org.springframework.stereotype.Controller;
   import org.springframework.web.bind.annotation.RequestMapping;
   import org.springframework.web.bind.annotation.RequestMethod;
   import org.springframework.web.servlet.ModelAndView;

   @Controller
   public class HomeController {

       @RequestMapping(value = "/", method = RequestMethod.GET)
       public String home() {
           return "home"; // returns the view name "home"
       }

       @RequestMapping(value = "/welcome", method = RequestMethod.GET)
       public String welcome() {
           return "welcome"; // returns the view name "welcome"
       }

       @RequestMapping(value = "/greeting", method = RequestMethod.GET)
       public ModelAndView greeting() {
           ModelAndView mav = new ModelAndView("greeting"); // view name
           mav.addObject("message", "Hello, World!"); // adding model data
           return mav;
       }
   }
   ```

2. **home.jsp** (view file for `home`):
   ```jsp
   <!DOCTYPE html>
   <html>
   <head>
       <title>Home</title>
   </head>
   <body>
       <h1>Welcome to the Home Page</h1>
   </body>
   </html>
   ```

3. **welcome.jsp** (view file for `welcome`):
   ```jsp
   <!DOCTYPE html>
   <html>
   <head>
       <title>Welcome</title>
   </head>
   <body>
       <h1>Welcome Page</h1>
   </body>
   </html>
   ```

4. **greeting.jsp** (view file for `greeting`):
   ```jsp
   <!DOCTYPE html>
   <html>
   <head>
       <title>Greeting</title>
   </head>
   <body>
       <h1>${message}</h1>
   </body>
   </html>
   ```

### Summary

- `@Controller` is used to define a Spring MVC controller.
- `@RequestMapping` maps web requests to handler methods.
- `ModelAndView` combines the model data and view name, allowing you to return both from a handler method.

This setup allows you to create a Spring MVC application that handles web requests, processes data, and renders views efficiently.