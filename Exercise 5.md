**Exercise 5: User privileges**


| Step | Actions                                                                                                                                                                                                                     |
|------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| a    | Create `Privilege` entity under package `domain`,having a field named _code_ of type string. This should be unique.                                                                                                         |
| b    | Associate each user with a list of privileges. A user may have many privileges, and a privilege may belong to many users. See https://vladmihalcea.com/the-best-way-to-map-a-onetomany-association-with-jpa-and-hibernate/. |
| c    | Deploy the service. Verify respective tables are automatically created in DB (you should have 2 new tables). Populate `Privileges` table with values `GUEST`, `EVEN`, `ODD`, `ADMIN`.                                       |
| d    | When a new user is created, he/she should get the following privileges:   <br/>- always the GUEST privilege  <br/> - choose randomly between the EVEN and ODD privileges (assign exactly 1 of them)                         |
| e    | When a user is deleted, verify that the association with his/her privileges is deleted as well (i.e. cascade).                                                                                                              |
| f    | Add new Unit Tests to verify the privilege logic and correct existing tests if needed.                                                                                                                                      |                                                                                      |
