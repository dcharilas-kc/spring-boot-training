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
[**Exercise 7: Service-to-service communication**](Exercise%207.md)
[**Exercise 8: Kafka notifications**](Exercise%208.md)



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


