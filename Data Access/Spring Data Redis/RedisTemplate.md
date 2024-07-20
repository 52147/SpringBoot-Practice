### Spring Data Redis

Spring Data Redis provides support for Redis, a key-value store.

#### Key Concepts

1. **RedisTemplate**
2. **@RedisHash**
3. **Key-Value Operations**

#### RedisTemplate

The `RedisTemplate` class provides operations for interacting with Redis.

- **Example**:
  ```java
  import org.springframework.data.redis.core.RedisTemplate;
  import org.springframework.beans.factory.annotation.Autowired;
  import org.springframework.stereotype.Service;

  @Service
  public class UserService {

      @Autowired
      private RedisTemplate<String, User> redisTemplate;

      public void save(User user) {
          redisTemplate.opsForValue().set(user.getId(), user);
      }

      public User findById(String id) {
          return redisTemplate.opsForValue().get(id);
      }
  }
  ```
