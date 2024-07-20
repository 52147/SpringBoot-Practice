#### SimpleJdbcInsert

The `SimpleJdbcInsert` class simplifies the insertion of data into a table.

- **Example**:
  ```java
  import org.springframework.jdbc.core.simple.SimpleJdbcInsert;
  import org.springframework.beans.factory.annotation.Autowired;
  import org.springframework.jdbc.core.namedparam.MapSqlParameterSource;
  import org.springframework.stereotype.Repository;

  @Repository
  public class UserRepository {

      @Autowired
      private SimpleJdbcInsert simpleJdbcInsert;

      public void save(User user) {
          MapSqlParameterSource parameters = new MapSqlParameterSource()
                  .addValue("name", user.getName())
                  .addValue("email", user.getEmail());
          simpleJdbcInsert.execute(parameters);
      }
  }
  ```
