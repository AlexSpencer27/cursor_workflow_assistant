# API Specification for Cursor Workflow Assistant Extension

This document defines the internal API contract for the extension. The API is used during both the design stage (to capture and validate requirements) and the autonomous agent coding stage (to generate production-ready, tested code). It leverages VSCode command registration and webview messaging for module communication.

## Base Domain
- The extension operates using VSCode commands and webview messaging to ensure smooth inter-module interactions.

## Command & Messaging Endpoints

### 1. Task Management API

#### GET /tasks
- **Purpose:** Retrieve the current list of development tasks.
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
- **Purpose:** Create a new task to guide development.
- **Payload:**
  ```json
  {
    "title": "New Task",
    "description": "Describe the task",
    "priority": "medium"
  }
  ```
- **Response:** 201 Created with the new task details.

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
- **Purpose:** Trigger a TDD check against the current code context.
- **Payload (optional override):**
  ```json
  {
    "override": true,
    "reason": "Provide a brief justification if needed."
  }
  ```
- **Response:**  
  Returns a warning if tests are missing unless an override is provided.

### 3. AI Prompt Optimization API

#### POST /prompt/optimize
- **Purpose:** Analyze the AI prompt and return an optimization score.
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
    "suggestions": "Optional suggestions for improvement."
  }
  ```

### 4. Code Review API

#### POST /review/trigger
- **Purpose:** Initiate a multi-character code review.
- **Payload:**
  ```json
  {
    "commitId": "uuid",
    "reviewMode": "onDemand | strict"
  }
  ```
- **Response:**  
  Returns review feedback from multiple personas and flags any conflicts for resolution.

## Error Handling
- **400 Bad Request:** Returned for validation errors.
- **500 Internal Server Error:** Returned for unhandled exceptions.
- All errors include a clear `error` message in the JSON payload. 