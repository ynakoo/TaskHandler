# Sequence Diagram

This diagram shows the end-to-end flow of the most critical system process: **Creating and Assigning a Task**.

## Diagram Visualization
![Sequence Diagram](file:///Users/ashwin/.gemini/antigravity/brain/3a2777b0-b452-475f-9cc3-48c4761664d2/sequence_diagram_v2.png)

## Mermaid Representation
You can recreate or edit this diagram using [Mermaid Live Editor](https://mermaid.live/).

```mermaid
sequenceDiagram
    autonumber
    actor Manager
    participant App as "Frontend App"
    participant API as "Backend API"
    participant DB as "Database"
    actor Member

    Manager->>App: Clicks "Create Task"
    App->>Manager: Displays Task Form
    Manager->>App: Enters Task Details (Title, Member ID, Deadline)
    App->>API: POST /api/tasks (JWT Token)
    
    API->>API: Validate Manager Permissions
    API->>DB: INSERT INTO tasks (title, assigned_to, deadline, status)
    DB-->>API: Success (task_id: 101)
    
    API-->>App: 201 Created (Success)
    App-->>Manager: Shows "Task Assigned Successfully"
    
    rect rgb(240, 248, 255)
    Note over API, Member: Asynchronous Notification
    API->>Member: Push Notification: "New Task Assigned"
    end
```
