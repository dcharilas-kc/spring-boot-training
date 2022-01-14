**Exercise 1: Hello World**

| Step | Actions                                                                                                                                                                                              |
|------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| a    | Create new Spring Boot project named `caller-service`. You can use https://start.spring.io/ for a quick setup.                                                                                       |
| b    | Verify that the project builds successfully (Maven/Gradle).                                                                                                                                          |
| c    | Verify that project can be started/deployed successfully. Default port should be _8080_, unless specified otherwise.                                                                                 |
| d    | Create `DemoController` class under package `controller`.                                                                                                                                            |
| e    | Add a new `GET` operation in the controller. The operation should not receive any input and return text as response body (`@ResponseBody`).   <br/>Make the operation return `"Hello World"`.        |
| f    | Create Unit Test to test the new operation. See https://spring.io/guides/gs/testing-web/ for some examples.   <br/> You should use `MockMvc` and verify that the output of the operation is correct. |
