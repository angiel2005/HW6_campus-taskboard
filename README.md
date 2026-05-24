# HW6 - Campus Task Board API
This assignment builds on Homework 5 by adding full database persistence, repository queries, pagination, search, and new filtering endpoints. The goal of this assignment was to learn how to use JPA entities, repositories, custom query methods, and H2 database integration while keeping the API clean and easy to test.

## Technologies Used
- Java 21 
- Spring Boot 
- Spring Web 
- Spring Data JPA 
- H2 Database (in‑memory)
- Maven 
- Postman (for testing)

## How to Run the Project
- Clone or download the project 
- Open in IntelliJ or VS Code 
- Run the Spring Boot application 
- API starts at: http://localhost:8080

To open the H2 console: http://localhost:8080/h2-console

Use: 
  - JDBC URL: jdbc:h2:mem:taskboarddb
  - Username: sa 
  - Password: (empty)

## API Endpoints
1. Create a Task

   POST /api/tasks  

   Creates a new task with validation on title and description.

3. Get All Tasks

   GET /api/tasks  

   Returns all tasks stored in the database.

4. Get Task by ID

   GET /api/tasks/{id}  

   Returns a single task or 404 if not found.

6. Update a Task

   PUT /api/tasks/{id}  

   Updates title, description, completed status, and priority.

7. Delete a Task

   DELETE /api/tasks/{id}  

   Deletes a task permanently (not soft delete in this assignment).

8. Get Completed Tasks

   GET /api/tasks/completed

9. Get Incomplete Tasks

   GET /api/tasks/incomplete

10. Filter by Priority
    GET /api/tasks/priority/{priority}
    Example: /api/tasks/priority/HIGH

11. Search Tasks (JPQL @Query)

GET /api/tasks/search?keyword=...

   Searches title + description (case‑insensitive).

12. Pagination + Sorting

    GET /api/tasks/paginated?page=0&size=5&sortBy=title

    Returns a Page<Task> with metadata:
    - totalElements 
    - totalPages 
    - size 
    - number 
    - first / last

## What I Learned
This assignment helped me understand how Spring Data JPA actually works behind the scenes. I learned how:
- JPA entities map directly to database tables 
- @Entity, @Id, @GeneratedValue, and @Column control how data is stored 
- Repositories automatically generate SQL queries from method names 
- @Query lets you write custom JPQL when naming conventions aren’t enough 
- Pagination and sorting are built into Spring through Pageable and Page 
- H2 is great for development because you can inspect everything instantly

## Challenges I Faced
- Understanding how PageRequest.of() works with sorting 
- Writing the JPQL search query so it ignores case

## Summary
This project demonstrates:

- Full CRUD with Spring Data JPA 
- Repository with custom query methods 
- Search filtering using JPQL 
- Pagination + sorting 
- H2 database integration
