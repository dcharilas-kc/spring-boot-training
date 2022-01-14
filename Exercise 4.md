**Exercise 4: Persist users**

For this exercise it is assumed that you have a DB in place. It can be any SQL DB, i.e. MySQL, Postgres, etc. Alternatively, you can use H2 as in-memory DB directly from inside the project.

If you wish, you can use Docker to set up containers in your PC, for example as described in https://phoenixnap.com/kb/mysql-docker-container.

If you are unfamiliar with the use of JPA and Hibernate, it is advised to read https://spring.io/guides/gs/accessing-data-rest/ before starting this exercise.

| Step | Actions                                                                                                                                                                                            |
|------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| a    | Add JPA libraries to the project and update configuration accordingly. (see https://www.baeldung.com/the-persistence-layer-with-spring-and-jpa)                                                    |
| b    | Mark the `User` class as entity by adding the `@Entity` class. Use the `@NotNull` annotation to indicate that field _name_ cannot be empty. Mark the _id_ field as auto-generated id.              |
| c    | Add new field _createdOn_ of type `LocalDateTime`. Use `@Temporal(TemporalType.TIMESTAMP)` annotation (or equivalent) to make sure dates are persisted properly.                                   |
| d    | Deploy the service and verify that the `User` table is created in DB automatically.                                                                                                                |
| e    | Create `UserRepository` class under package `repository`. Add methods for all required operations included in `UserService`.                                                                       |
| f    | Create `PersistentUserService` class under package `service` and add the same methods as `UserService`. Instead of maintaining a hardcoded list of users, this service will call `UserRepository`. |
| g    | Create Unit Tests for `PersistentUserService` by mocking `UserRepository`.                                                                                                                         |
| h    | Change `UserController` so that it calls `PersistentUserService` instead of `UserService`.                                                                                                         |
| i    | If needed, make any necessary changes to Unit Tests so that no errors exist.                                                                                                                       |
| j    | Deploy the service and test the new operations manually (e.g. using Postman). Verify data correctness in DB.                                                                                       |

