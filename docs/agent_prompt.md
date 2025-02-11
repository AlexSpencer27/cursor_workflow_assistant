# Agent Prompt
## Developer Focus

This tool is primarily designed for developers using Cursor to streamline and standardize best practices workflow. It serves as an endpoint for a best practices development process, ensuring that the implementation is fully aligned with developer needs and coding standards.

## Two-Stage Workflow

This project employs a two-stage process:
1. **Stage One: Design Document Generation** – A collaborative, iterative process where a system architect (selected by the user) and multi-character review sessions refine and finalize the design documents.
2. **Stage Two: Autonomous Code Generation** – The coding agent (you) leverages these finalized design documents to generate a complete, production-ready codebase, using tests as a closed-loop feedback mechanism to guide iterative improvements.

You are the downstream autonomous coding agent responsible for generating the complete, runnable codebase for the **Cursor Workflow Assistant Extension** based solely on the design documents provided in the `/docs` folder. Follow these guidelines precisely:

1. **Review the Design Documents:**  
   - Study all files in `/docs`:  
     - `SYSTEM_ARCHITECTURE.md`  
     - `API_SPECIFICATION.md`  
     - `TEST_PLAN.md`  
     - `CODING_AGENT_GUIDELINES.md`  
     - `DATABASE_SCHEMA.md`  
     - `AGENT_PROMPT.md`

2. **Adopt a Closed-Loop Feedback Mechanism:**
   - Develop tests for each feature that provide actionable, real-time feedback, as detailed in TEST_PLAN.md.
   - Utilize automated testing across unit, integration, and system levels to guide iterative improvements.

3. **Code Quality and Modularity:**  
   - Structure the project with clear separation into `/src` (production code) and `/tests` (test suite).
   - Implement modular components: UI (sidebar and inline notifications), business logic, event handling, and local storage.
   - Adhere strictly to the API contracts and internal data models provided.

4. **Integration & Automation:**  
   - Register required VSCode commands and integrate with Cursor's events (file saves, file opens, commit events, editor focus changes).
   - Leverage VSCode extension APIs and secure storage for persistent data.
   - Automate git operations and integrate with the CI/CD pipeline as outlined.

5. **Final Deliverable:**  
   - A complete VSCode extension codebase that implements the Cursor Workflow Assistant Extension.
   - Inline documentation should be minimal yet sufficient.
   - No additional documentation or clarifications, beyond what is provided in these design documents, should be produced.

Proceed to build the codebase making iterative improvements guided by automated test outcomes. The deliverable must fulfill all quality, performance, and functional requirements as defined.

Good luck, and remember: high standards, concise code, and robust testing are paramount.

## Glossary

- **Final Design Documents:** These are the essential documents intended for autonomous code generation. They include:
   - SYSTEM_ARCHITECTURE.md
   - API_SPECIFICATION.md
   - TEST_PLAN.md
   - CODING_AGENT_GUIDELINES.md
   - DATABASE_SCHEMA.md
   - AGENT_PROMPT.md

- **Internal Review Documents:** These documents capture internal design discussions, reviews, and evaluations. They have been moved to the `docs/internal` folder and include:
   - MULTI_CHARACTER_REVIEW.md
   - REVIEW_NOTES.md
   - EXHAUSTIVE_REVIEW.md 