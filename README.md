# 📋 Task Manager
<span>
  <img src="https://img.shields.io/badge/Java-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white"/>
  <img src="https://img.shields.io/badge/apache_maven-C71A36?style=for-the-badge&logo=apachemaven&logoColor=white"/>
  <img src="https://img.shields.io/badge/Spring_Boot-6DB33F?style=for-the-badge&logo=spring-boot&logoColor=white"/>
</span> <br><br>

A RESTful API built with Spring Boot for managing tasks (create, read, update, delete), backed by an embedded H2 database. 

---

## ✅ Requirements
- [JDK 21](https://www.oracle.com/java/technologies/javase/jdk21-archive-downloads.html) installed

> No need to install Maven separately. This project includes the Maven Wrapper (`mvnw`).
> No need to install a database. It uses an embedded H2 database.

## ⚙️ How to Run

1. Clone the repository
```bash
git clone https://github.com/artknak/task-manager.git
cd task-manager
```

2. Run the application
```bash
# Linux/Mac
./mvnw spring-boot:run

# Windows
mvnw.cmd spring-boot:run
```

> On Linux/Mac, if you get a "Permission denied" error, run `chmod +x mvnw` first.

3. The API will be available at `http://localhost:8080`

## 🛠️ How to Use

A Postman collection is available [here](https://documenter.getpostman.com/view/49061873/2sB3QKrVRm) to test the endpoints.

### 🔍 Get All Tasks
Get all tasks currently saved.
```bash
GET http://localhost:8080/task
```
Example response:
```json
{
    "msg": "Tasks retrieved successfully.",
    "data": [
        {
            "id": 1,
            "name": "Do summary",
            "dueDate": "2025-10-12",
            "responsible": "Artur"
        },
        {
            "id": 2,
            "name": "Refactor code",
            "dueDate": "2025-10-15",
            "responsible": "John"
        },
        {
            "id": 3,
            "name": "Send email to professor",
            "dueDate": "2025-10-10",
            "responsible": "Maria"
        }
    ]
}
```

### 🔍 Get Task By Id
Get a single task by adding its ID after the endpoint.
```bash
GET http://localhost:8080/task/1
```
Example response:
```json
{
    "msg": "Task retrieved successfully.",
    "data": {
        "id": 1,
        "name": "Do summary",
        "dueDate": "2025-10-12",
        "responsible": "Artur"
    }
}
```

### 📝 Create Task
Create a task.
```bash
POST http://localhost:8080/task
Content-Type: application/json
```
```json
{
  "name": "Test",
  "dueDate": "2025-11-20",
  "responsible": "Gabriela"
}
```
Example response:
```json
{
    "msg": "Task created successfully.",
    "data": {
        "id": 4,
        "name": "Test",
        "dueDate": "2025-11-20",
        "responsible": "Gabriela"
    }
}
```

### ✏️ Update Task
Update a task by adding its ID after the endpoint.
```bash
PUT http://localhost:8080/task/1
Content-Type: application/json
```
```json
{
  "name": "Updated task",
  "dueDate": "2025-10-25",
  "responsible": "Carlos"
}
```
Example response:
```json
{
    "msg": "Task updated successfully.",
    "data": {
        "id": 1,
        "name": "Updated task",
        "dueDate": "2025-10-25",
        "responsible": "Carlos"
    }
}
```

### 🗑️ Delete Task By Id
Delete a single task by adding its ID after the endpoint.
```bash
DELETE http://localhost:8080/task/1
```
Example response:
```json
{
    "msg": "Task deleted successfully.",
    "data": null
}
```

### 🗑️ Delete All Tasks
Delete all tasks.
```bash
DELETE http://localhost:8080/task
```
Example response:
```json
{
    "msg": "All tasks deleted successfully.",
    "data": null
}
```
