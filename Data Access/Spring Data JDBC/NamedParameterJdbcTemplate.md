#### NamedParameterJdbcTemplate

The `NamedParameterJdbcTemplate` class provides named parameters support for queries and updates.

- **Example**:
  ```java
  import org.springframework.jdbc.core.namedparam.NamedParameterJdbcTemplate;
  import org.springframework.beans.factory.annotation.Autowired;
  import org.springframework.stereotype.Repository;

  @Repository
  public class UserRepository {

      @Autowired
      private NamedParameterJdbcTemplate namedParameterJdbcTemplate;

      public User findById(Long id) {
          String sql = "SELECT * FROM users WHERE id = :id";
          MapSqlParameterSource parameters = new MapSqlParameterSource().addValue("id", id);
          return namedParameterJdbcTemplate.queryForObject(sql, parameters, (rs, rowNum) ->
                  new User(rs.getLong("id"), rs.getString("name"), rs.getString("email")));
      }

      public void save(User user) {
          String sql = "INSERT INTO users (name, email) VALUES (:name, :email)";
          MapSqlParameterSource parameters = new MapSqlParameterSource()
                  .addValue("name", user.getName())
                  .addValue("email", user.getEmail());
          namedParameterJdbcTemplate.update(sql, parameters);
      }
  }
  ```
