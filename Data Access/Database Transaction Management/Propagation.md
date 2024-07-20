#### Propagation

Propagation defines how transactions relate to each other. Spring supports various propagation behaviors, such as:

- **REQUIRED**: Use the current transaction, create a new one if none exists (default).
- **REQUIRES_NEW**: Create a new transaction, suspending the current transaction if one exists.
- **MANDATORY**: Use the current transaction, throw an exception if none exists.
- **NESTED**: Execute within a nested transaction if a current transaction exists.
- **NOT_SUPPORTED**: Execute non-transactionally, suspending the current transaction if one exists.
- **NEVER**: Execute non-transactionally, throw an exception if a transaction exists.

- **Example**:
  ```java
  @Transactional(propagation = Propagation.REQUIRES_NEW)
  public void saveWithNewTransaction(User user) {
      userRepository.save(user);
  }
  ```
