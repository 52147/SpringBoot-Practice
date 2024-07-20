### RESTful APIs Overview with Status Codes

RESTful APIs (Representational State Transfer) are a set of architectural principles and guidelines used for designing networked applications, particularly in web development. They enable communication and data exchange between client applications and servers using standard HTTP methods. An important aspect of RESTful APIs is the use of HTTP status codes to indicate the result of the client's request.

### Key Concepts and Characteristics of RESTful APIs

1. **Resource-Based**

   RESTful APIs treat everything as a resource, which can be an object, a collection of objects, or any other identifiable entity. Each resource is uniquely identified by a URL (Uniform Resource Locator).

   - **Example**: In a blogging application, resources could include posts, comments, and users.
     - URL for a specific post: `/posts/123`
     - URL for comments on a specific post: `/posts/123/comments`

2. **Stateless**

   The server does not store any client state. Each request from the client contains all the necessary information for the server to process it. This approach allows for scalability and easy load balancing in distributed systems.

   - **Example**: A request to get a user's profile must include all necessary authentication and state information within the request itself.

3. **HTTP Verbs**

   RESTful APIs use standard HTTP methods, also known as verbs, to perform actions on resources. The commonly used methods are:

   - **GET**: Retrieve a representation of a resource.
     - `GET /users/1` – Retrieve user with ID 1.
   - **POST**: Create a new resource.
     - `POST /users` – Create a new user.
   - **PUT**: Update an existing resource.
     - `PUT /users/1` – Update user with ID 1.
   - **DELETE**: Remove a resource.
     - `DELETE /users/1` – Delete user with ID 1.
   - **PATCH**: Partially update a resource.
     - `PATCH /users/1` – Partially update user with ID 1.

4. **Uniform Interface**

   RESTful APIs follow a uniform and consistent interface, providing a standardized way to interact with resources. This interface typically includes self-descriptive messages, allowing clients to understand how to interact with resources based on the provided representations (e.g., JSON or XML).

   - **Example**: A response from a RESTful API might include links to related resources:
     ```json
     {
       "id": 1,
       "name": "John Doe",
       "links": {
         "self": "/users/1",
         "posts": "/users/1/posts"
       }
     }
     ```

5. **Hypermedia as the Engine of Application State (HATEOAS)**

   This principle suggests that a client should be able to navigate the API's resources dynamically by following hyperlinks contained within the API responses. It allows for a more flexible and decoupled interaction between clients and servers.

   - **Example**: A response for a user might include links to perform further actions:
     ```json
     {
       "id": 1,
       "name": "John Doe",
       "links": {
         "self": "/users/1",
         "update": "/users/1/update",
         "delete": "/users/1/delete"
       }
     }
     ```

### Common HTTP Status Codes in RESTful APIs

- **200 OK**: The request was successful.
  - **Example**: `GET /users/1` returns the user data with a 200 status code.
- **201 Created**: A new resource has been created successfully.
  - **Example**: `POST /users` returns a 201 status code when a new user is created.
- **204 No Content**: The request was successful, but there is no content to send in the response.
  - **Example**: `DELETE /users/1` returns a 204 status code when a user is deleted.
- **400 Bad Request**: The request could not be understood or was missing required parameters.
  - **Example**: `POST /users` with invalid data returns a 400 status code.
- **401 Unauthorized**: Authentication failed or user does not have permissions for the desired action.
  - **Example**: Accessing a protected resource without valid authentication returns a 401 status code.
- **404 Not Found**: The requested resource could not be found.
  - **Example**: `GET /users/999` for a non-existent user returns a 404 status code.
- **500 Internal Server Error**: An error occurred on the server.
  - **Example**: A server malfunction or unhandled exception returns a 500 status code.

### Complete Example with Status Codes

Below is a complete example of a Spring Boot application that creates RESTful web services with appropriate status codes.

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

       public boolean deleteById(Long id) {
           return users.removeIf(user -> user.getId().equals(id));
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
       public ResponseEntity<List<User>> getAllUsers() {
           List<User> users = userService.findAll();
           return new ResponseEntity<>(users, HttpStatus.OK);
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

       @PutMapping("/users/{id}")
       public ResponseEntity<User> updateUser(@PathVariable Long id, @RequestBody User user) {
           User existingUser = userService.findById(id);
           if (existingUser == null) {
               return new ResponseEntity<>(HttpStatus.NOT_FOUND);
           }
           existingUser.setName(user.getName());
           existingUser.setEmail(user.getEmail());
           userService.save(existingUser);
           return new ResponseEntity<>(existingUser, HttpStatus.OK);
       }

       @DeleteMapping("/users/{id}")
       public ResponseEntity<Void> deleteUser(@PathVariable Long id) {
           boolean isDeleted = userService.deleteById(id);
           if (!isDeleted) {
               return new ResponseEntity<>(HttpStatus.NOT_FOUND);
           }
           return new ResponseEntity<>(HttpStatus.NO_CONTENT);
       }
   }
   ```

### Summary

- RESTful APIs provide a standardized and flexible approach for building web services, allowing for efficient and scalable communication between clients and servers.
- Key concepts include resource-based design, statelessness, HTTP verbs, a uniform interface, and HATEOAS.
- Common HTTP status codes used in RESTful APIs include 200 OK, 201 Created, 204 No Content, 400 Bad Request, 401 Unauthorized, 404 Not Found, and 500 Internal Server Error.
- A complete example demonstrates how to create a Spring Boot RESTful service with appropriate status codes.