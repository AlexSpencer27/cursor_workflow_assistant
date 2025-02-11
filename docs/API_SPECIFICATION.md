# API Specification for Cursor Workflow Assistant Extension

This document defines the internal API contract for modules within the extension. Although the extension operates locally within VSCode, it exposes a set of command interfaces and internal endpoints to manage tasks, enforce TDD, and handle review feedback.

## Base Domain
- The extension utilizes VSCode command registration and webview messaging to communicate between modules.

## Command & Messaging Endpoints

### 1. Task Management API

#### GET /tasks
- **Purpose:** Retrieve the current list of tasks.
- **Response Example:**
  ```json
  {
    "tasks": [
      {
        "id": "uuid",
        "title": "Write Unit Tests",
        "description": "Generate test stubs for the new module",
        "status": "pending",
        "priority": "high",
        "createdAt": "ISO8601 timestamp",
        "updatedAt": "ISO8601 timestamp"
      }
    ]
  }
  ```

#### POST /tasks
- **Purpose:** Create a new task.
- **Payload:**
  ```json
  {
    "title": "New Task",
    "description": "Describe the task",
    "priority": "medium"
  }
  ```
- **Response:**  
  - 201 Created with the task object.

#### PUT /tasks/{id}
- **Purpose:** Update an existing task.
- **Payload:**
  ```json
  {
    "title": "Updated Task Title",
    "description": "Updated description",
    "status": "completed",
    "priority": "high"
  }
  ```
- **Response:** 200 OK with the updated task.

#### DELETE /tasks/{id}
- **Purpose:** Delete a task.
- **Response:** 204 No Content.

### 2. TDD Enforcement API

#### POST /tdd/check
- **Purpose:** Trigger a TDD check for the current code context.
- **Payload (optional override):**
  ```json
  {
    "override": true,
    "reason": "Brief explanation, if required."
  }
  ```
- **Response:**  
  - If tests are missing and not overridden, return a warning message.
  - Otherwise, acknowledge the override.

### 3. AI Prompt Optimization API

#### POST /prompt/optimize
- **Purpose:** Analyze and return a score for the AI prompt.
- **Payload:**
  ```json
  {
    "promptText": "Your prompt text here"
  }
  ```
- **Response:**  
  ```json
  {
    "score": "green | yellow | red",
    "suggestions": "Optional detailed suggestions for improvement."
  }
  ```

### 4. Code Review API

#### POST /review/trigger
- **Purpose:** Initiate a multi-persona code review.
- **Payload:**
  ```json
  {
    "commitId": "uuid",
    "reviewMode": "onDemand | strict"
  }
  ```
- **Response:**  
  - Collection of review feedback from different personas.
  - In case of conflicting feedback, provide a flag for conflict resolution.

## Error Handling
- **400 Bad Request:** For validation errors.
- **500 Internal Server Error:** For unhandled exceptions.
- All error responses include a clear `error` message in the JSON payload. 