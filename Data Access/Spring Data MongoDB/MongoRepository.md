### Spring Data MongoDB

Spring Data MongoDB simplifies working with MongoDB in Spring applications.

#### Key Concepts

1. **MongoRepository**
2. **@Document**
3. **@Field**

#### MongoRepository

The `MongoRepository` interface provides CRUD operations for MongoDB.

- **Example**:
  ```java
  import org.springframework.data.mongodb.repository.MongoRepository;

  public interface UserRepository extends MongoRepository<User, String> {
  }
  ```

