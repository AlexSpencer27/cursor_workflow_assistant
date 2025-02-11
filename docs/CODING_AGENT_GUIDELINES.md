# Coding Agent Guidelines for Cursor Workflow Assistant Extension

**Note:** For autonomous code generation, please refer only to the final design documents in this folder. Internal review documents have been relocated to the `docs/internal` folder and are not part of the operational guidelines.

This document provides detailed instructions for the AI coding agent tasked with generating the full VSCode extension codebase based on these design documents.

## Core Instructions

1. **Closed-Loop Feedback Mechanism**
   - Develop tests that provide actionable, real-time feedback to guide iterative improvements, especially for event handling and UI notifications.

2. **Modular Code & Minimalism**
   - Implement each module (task management, TDD enforcement, AI prompt optimization, and multi-persona code review) as a separate, self-contained unit.
   - Remove or refactor redundant or overly complex code, favoring clarity and brevity.
   - Ensure clear separation of concerns between UI components, core functionality modules, and integration/event handling.

3. **Project Structure**
   - **/src:** All production code.
   - **/tests:** Comprehensive test cases.
   - Use VSCode's recommended project structure for extensions.
   - Organize code with clear command registrations and message passing mechanisms.

4. **Version Control & CI/CD**
   - Automate git operations: branching, committing, and pushing.
   - Integrate a CI/CD pipeline to run automated tests on every commit.
   - Implement auto-rollback if three consecutive builds or tests fail.

5. **Coding Standards**
   - Use TypeScript with strict type checking.
   - Apply a consistent coding style enforced by linters (e.g., ESLint).
   - Embed concise inline documentation where necessary.

6. **API & Integration Compliance**
   - Adhere strictly to the API contracts as defined in `API_SPECIFICATION.md`.
   - Validate and sanitize inputs and provide thorough error handling.

7. **Performance & Security**
   - Ensure that response times for UI notifications and validations are under 200ms.
   - Use VSCode secure storage APIs for any persisted data.
   - Implement debouncing/throttling on event handlers to manage rapid file changes.

8. **Final Deliverable**
   - A complete, runnable VSCode extension codebase that implements the Cursor Workflow Assistant Extension.
   - Inline documentation should be minimal yet sufficient.
   - No additional documentation or clarifications, beyond what is provided in these design documents, should be produced. 