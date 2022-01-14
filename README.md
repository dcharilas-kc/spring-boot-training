This series of exercises is addressed to people who are familiar with _Java_ and have a basic understanding of _Spring_ / _Spring Boot_.   
They are intended to be performed in sequence, as each exercise builds on top of the code created by the previous ones.  
Guidelines become less specific as the exercises move on, providing only hints and useful links in some cases. The purpose is to encourage the engineer to search for online guides and then reflect on what the best solution would be in order to cover the exercises' requirements. 
The code is to be reviewed by a Senior colleague after completion of each exercise and feedback should be provided, before moving on to the next exercise. 

For some exercises software installation is required (e.g. Kafka, DB).For those it is advised to use Docker containers, as out-of-the-box solutions.


[**Exercise 1: Hello World**](Exercise%201.md)   
[**Exercise 2: Fetch user(s) API**](Exercise%202.md)   
[**Exercise 3: User management API**](Exercise%203.md)   
[**Exercise 4: Persist users**](Exercise%204.md)   
[**Exercise 5: User privileges**](Exercise%205.md)   
[**Exercise 6: Scheduler**](Exercise%206.md)

**Exercise 7: Kafka notifications**

7a. Add kafka libraries to the project and update configuration accordingly (both producer and consumer). Define different topics to write and read. The idea is that the service should a) inform others whenever a job is done b) receive command by others to perform actions.
7b. Create new POJO for notification with id, action enum (ADD,DELETE) and status enum (COMPLETED,PENDING)
7c. Upon successful completion of add/delete user operation, dispatch a proper message to Kafka (status COMPLETED). Dispatch should be asynchronous so as not to interfere with the operation execution.
7d. Create Kafka consumer. Upon receipt of message with status PENDING, invoke add/delete operation.
7f. Verify Unit Tests are not broken! Add Kafka mock if needed.

**Exercise 9: Expose Web Service**

9a. Read the following guide: https://spring.io/guides/gs/producing-web-service/. Create web service to expose operation getUserById, which will receive an id as input and return a user object.
9b. Generate WSDL file
9c. Input and output will be in xml format, as specified by the SOAP protocol.
9d. Test the new web service by Postman or SoapUi, by making a SOAP request.

**Exercise 10: Internal microservice communication**

10a. Create a new microservice (we will call them A and B from now on)
10b. In B, use the previously generated WSDL to generate stubs. You can do this during build time by using proper plugin in pom, e.g. maven-jaxb2-plugin
10c. In B, invoke get user REST operation of A. You can use Feign client or invoke directly RestTemplate to achieve this. For example: https://spring.io/guides/gs/consuming-rest/
10d. In B, invoke get user SOAP operation of A. For example: https://www.baeldung.com/spring-soap-web-service, https://spring.io/guides/gs/consuming-web-service/
10e. Compare results for above operations. For the same id, retrieved used information should be identical

**Exercise 11: Database migrations**

11a. All changes of this exercise concern B. Add JDBC libs and related configuration. Make sure that tables are NOT automatically created during Spring Boot initialization.
11b. Add Flyway libs and configuration. Make sure that you create the flyway migrations table in DB (this should be the very first script). Write a script that creates table REQUEST_AUDIT, with columns ID, TIMESTAMP, REPONSE. All names need to be EXACTLY as shown.
11c. Whenever the operation calling A in invoked, write a record in the new table, using JPA repository. The result of the call should be stored in the REPONSE column. 
11d. Add a new script in Flyway that adds a new column named REQ_PROTOCOL in table REQUEST_AUDIT and corrects the typo of REPONSE to RESPONSE. After running Spring Boot, check the contents of migrations table. 
11e. Update code so that whenever a new record is added, column REQ_PROTOCOL is filled with either REST or SOAP

**Exercise 12: Caching**

12a. All changes of this exercise concern B. Add libs to support Redis (you will need a local installation of Redis for testing purposes).
12b. Create a cachable object (@RedisHash) that lives for 60 seconds (@TimeToLive). This should contain user response for a specific user id. 
12c. Update the SOAP operation only. Whenever a response is received, store it in the cache. Before making the call, check the cache. If found, the return this information instead of calling A.
12d. Verify this logic works. REST calls should always be made. SOAP calls should be made the 1st time for a user, but not subsequent ones. Verify that the cache expires after 60 seconds (calls to A should be made again).


