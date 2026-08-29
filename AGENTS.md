# AGENTS.md — ASI OS Development Rules

## Mission
Build a modular, secure, testable agentic operating layer. Prefer composable primitives over monolithic agents.

## Rules

1. Treat LLMs as reasoning components, not trusted executors.
2. Every external action must be represented by a typed Tool and/or MCP capability.
3. Skills describe workflows; tools perform atomic actions.
4. Apply least privilege and explicit policy checks before execution.
5. Never introduce unrestricted shell, filesystem or network access as a default.
6. Keep provider-specific logic behind adapters.
7. Prefer deterministic validation and tests after agent-generated changes.
8. Make destructive operations explicit and approval-gated.
9. Record tool calls, outcomes, errors and approvals in an auditable event model.
10. Avoid leaking secrets into prompts, logs or repository files.
11. Version schemas and preserve backward compatibility where practical.
12. Keep architecture documentation synchronized with implementation changes.
