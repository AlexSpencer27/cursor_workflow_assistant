# Coding Agent Guidelines for Cursor Workflow Assistant Extension

This document details the instructions for the autonomous coding agent. The agent uses the finalized design documents from Stage One to generate a complete, production-ready VSCode extension. A strict Test-Driven Development (TDD) methodology guides the build.

## Core Instructions

1. **Closed-Loop Feedback Mechanism**
   - Develop tests that offer real-time, actionable feedback.
   - Ensure every new feature or integration point is developed using TDD.

2. **Modular Code & Minimalism**
   - Implement each feature (task management, TDD enforcement, AI prompt optimization, and multi-character code review) as a self-contained module.
   - Refactor or remove redundant/complex code to maintain clarity.
   - Clearly separate UI components, core business logic, and event handling.

3. **Project Structure**
   - **/src:** Contains all production code.
   - **/tests:** Contains comprehensive unit, integration, and system tests.
   - Follow VSCode's recommended project layout with clear command registration and message-passing structures.

4. **Version Control & CI/CD**
   - Automate git operations (branching, committing, and pushing).
   - Integrate with a CI/CD pipeline that runs automated tests on every commit.
   - Implement auto-rollback if three consecutive builds or tests fail.

5. **Coding Standards**
   - Use TypeScript with strict type checking.
   - Enforce a consistent coding style using linters (e.g., ESLint).
   - Provide concise inline documentation for non-obvious logic.

6. **API & Integration Compliance**
   - Adhere strictly to the API contracts defined in `API_SPECIFICATION.md`.
   - Validate and sanitize all inputs robustly with thorough error handling.

7. **Performance & Security**
   - Ensure that UI notifications and validations are responsive (<200ms).
   - Use VSCode secure storage APIs for any persisted data.
   - Implement debouncing and throttling for event handlers during high-frequency operations.

8. **Final Deliverable**
   - Produce a complete, runnable VSCode extension codebase that complies with the design documents.
   - Inline documentation should be succinct but sufficient.
   - No additional documentation should be generated beyond what is provided.

## Two-Stage Process Overview
- **Stage One: Design** – Finalize design documents via brainstorming, technical deep dive, and iterative multi-character reviews.
- **Stage Two: Agent Coding** – Generate production-ready code based entirely on the approved design documents. 