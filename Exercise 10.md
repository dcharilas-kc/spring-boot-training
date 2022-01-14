**Exercise 10: Caching (Redis)**

For this exercise it is assumed that you have Redis installed (https://redis.io/download).
Alternatively, you can use Docker https://medium.com/idomongodb/installing-redis-server-using-docker-container-453c3cfffbdf.

If you are not interested in learning more about caching, feel free to skip this exercise.

All the below steps are meant for `caller-service`.

| Step | Actions                                                                                                                                                                                                                                                                                    |
|------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| a    | Add Redis libraries (see https://www.baeldung.com/spring-boot-redis-cache). Create `CacheConfig` class under package `config`. Do not forget to add `@EnableCaching`.                                                                                                                      |
| b    | Create `UserDetails` class under package `cache`. Add proper annotations so that the object is cacheable (`@RedisHash`) and lives in cache for 60 seconds (`@TimeToLive`). The class should have only 1 field, named response.                                                             |
| c    | Create `UserRepository` class under package `cache`. Add operation to retrieve user details by id (see https://www.baeldung.com/spring-data-redis-tutorial).                                                                                                                               |
| d    | Update the logic as follows: <br/> - whenever `caller-service` is asked for user information, check if it exists in Redis. <br/>   # if it does, return this instead of calling `user-service`.  <br/>   # if it does not, call `user-service`, store the response in Redis and log in DB. |
| e    | Verify the caching logic works. You can use `REQUEST_AUDIT` from Exercise 9 for easy testing. Keep in mind that the caching should be applied only for 60 seconds.                                                                                                                         |
