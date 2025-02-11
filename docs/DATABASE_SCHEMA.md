# Internal Data Model for Cursor Workflow Assistant Extension

This document defines the internal schema used for persistent storage within the extension. Data is stored using VSCode's extension storage APIs (global and workspace states).

## Entities

### 1. Task Entity
- **Purpose:** Manage tasks that guide the developer through required steps (e.g., TDD checks, review reminders).
- **Schema:**
  - `id` (string, UUID): Unique task identifier.
  - `title` (string): Brief and descriptive title.
  - `description` (string, optional): Detailed task description.
  - `status` (string): Task status (e.g., "pending", "in_progress", "completed").
  - `priority` (string): Priority level (e.g., "low", "medium", "high").
  - `tags` (array of strings, optional): Categories such as "frontend", "backend", "urgent".
  - `createdAt` (timestamp): Creation time.
  - `updatedAt` (timestamp): Last updated time.
  - `subTasks` (array of Task Entities, optional): For nested task management.

### 2. Configuration Entity
- **Purpose:** Store user settings and configuration options.
- **Schema:**
  - `tddStrictMode` (boolean): Indicates if strict TDD enforcement is enabled.
  - `reviewFrequency` (string): "onDemand", "perCommit", or "periodic".
  - `inlineNotificationStyle` (object): Customization options for notification appearance (e.g., duration, color coding).
  - `uiPreferences` (object): Sidebar settings such as visibility, size, and theme adjustments.

### 3. Review Log Entity
- **Purpose:** Archive multi-persona review outcomes and conflict resolution details.
- **Schema:**
  - `id` (string, UUID): Unique log identifier.
  - `commitId` (string, optional): Reference to the commit or code change.
  - `reviews` (object): Contains feedback from each defined persona:
    - `systemArchitect`: Feedback text.
    - `downstreamCodingAgent`: Feedback text.
    - `aiAgentSimulator`: Feedback text.
    - `downstreamUser`: Feedback text.
  - `timestamp` (timestamp): Time of review.
  - `conflictResolved` (boolean): Indicator if conflicts were addressed by the user. 