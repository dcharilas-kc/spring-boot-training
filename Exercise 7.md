**Exercise 7: Service-to-service communication**


| Step | Actions                                                                                                                                                                                                                                                        |
|------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| a    | Create new microservice named `caller-service`. Make sure that it listens to a different port than `user-service`, by updating `application.yml` or `application.properties`. All the following steps of this exercise should be performed on this service.    |
| b    | Add libraries for `RestTemplate`. More information can be found in https://spring.io/guides/gs/consuming-rest/. Create `RestConfig` class under package `config` in order to create appropriate `Bean`.                                                        |
| c    | Create `UserController` class under package `controller` and `UserService` under package `service`. Create new `GET` operation in `UserController` that calls `UserService` and returns a single user in JSON format. Operation will receive user id as input. |
| d    | Invoke `user-service` in order to retrieve user information. You should use `getForObject` method of `RestTemplate` to invoke the proper operation.                                                                                                            |
| e    | Test the new service manually to verify data is retrieved from `user-service` successfully.                                                                                                                                                                    |

