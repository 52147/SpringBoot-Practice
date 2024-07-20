### Spring Data JPA

Spring Data JPA is a part of the larger Spring Data family, designed to simplify the development of data access layers in Java applications. It reduces boilerplate code and provides a consistent programming model for working with various data stores.

#### Key Concepts

1. **@Entity**
2. **JpaRepository**
3. **CrudRepository**
4. **@Query**

#### @Entity

The `@Entity` annotation is used to map a class to a database table. Each instance of the class corresponds to a row in the table.

- **Example**:
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
