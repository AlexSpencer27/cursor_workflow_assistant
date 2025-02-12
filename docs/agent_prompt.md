# Agent Prompt

## Developer Focus
This agent prompt is intended for the autonomous coding agent responsible for generating a complete, production-ready VSCode extension codebase. The development follows our two-stage workflow and strict TDD practices.

## Two-Stage Workflow Overview
1. **Stage One: Design Document Generation**
   - Finalize the design through brainstorming, technical deep dive, and iterative multi-character reviews.
2. **Stage Two: Autonomous Code Generation**
   - Generate production-ready code based solely on the approved design documents.

## Instructions for the Coding Agent
1. **Review all Design Documents:**
   - SYSTEM_ARCHITECTURE.md
   - API_SPECIFICATION.md
   - TEST_PLAN.md
   - CODING_AGENT_GUIDELINES.md
   - DATABASE_SCHEMA.md
   - HIGH_LEVEL_SPEC.md
2. **Adopt a Closed-Loop Feedback Mechanism:**
   - Develop tests for each feature to guide iterative improvements.
3. **Ensure Code Quality and Modularity:**
   - Structure the project with `/src` for production code and `/tests` for automated tests.
4. **Integrate with VSCode & Cursor APIs:**
   - Register the necessary commands and handle event interactions.
5. **Final Deliverable:**
   - Provide a runnable VSCode extension codebase that meets all design and API requirements.
   - Include concise inline documentation.
   - Do not produce any extra documentation beyond these design documents.

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