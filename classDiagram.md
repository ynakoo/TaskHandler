# Class Diagram (UML)

The Class Diagram outlines the major classes, their attributes, methods, and the relationships (Inheritance, Association, Composition) between them. This focuses on the OOP principles required for the backend.


```mermaid
classDiagram
    class User {
        <<Abstract>>
        -int id
        -string username
        -string email
        -string passwordHash
        +login()
        +logout()
    }

    class Admin {
        +manageUsers()
        +configureRoles()
    }

    class Manager {
        +createProject()
        +assignTask()
    }

    class Member {
        +updateTaskStatus()
        +addComment()
    }

    User <|-- Admin
    User <|-- Manager
    User <|-- Member

    class Project {
        -int id
        -string name
        -string description
        +addMember()
    }

    class Task {
        -int id
        -string title
        -string status
        -date deadline
        +changeStatus()
    }

    class Comment {
        -int id
        -string content
        -datetime timestamp
    }

    Project "1" *-- "many" Task : contains
    Task "1" *-- "many" Comment : has
    Member "1" -- "0..*" Task : assigned to
```
