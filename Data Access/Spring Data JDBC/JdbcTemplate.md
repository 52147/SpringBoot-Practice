### Spring Data JDBC

Spring Data JDBC provides simplified access to relational databases using JDBC.

#### Key Concepts

1. **JdbcTemplate**
2. **SimpleJdbcInsert**
3. **NamedParameterJdbcTemplate**

#### JdbcTemplate

The `JdbcTemplate` class provides methods for querying and updating the database.

- **Example**:
  ```java
  import org.springframework.jdbc.core.JdbcTemplate;
  import org.springframework.beans.factory.annotation.Autowired;
  import org.springframework.stereotype.Repository;

  @Repository
  public class UserRepository {

      @Autowired
      private JdbcTemplate jdbcTemplate;

      public User findById(Long id) {
          return jdbcTemplate.queryForObject("SELECT * FROM users WHERE id = ?", new Object[]{id}, (rs, rowNum) ->
                  new User(rs.getLong("id"), rs.getString("name"), rs.getString("email")));
      }

      public void save(User user) {
          jdbcTemplate.update("INSERT INTO users (name, email) VALUES (?, ?)", user.getName(), user.getEmail());
      }
  }
  ```
