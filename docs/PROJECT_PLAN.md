# ASI OS Project Plan

## Goal
Create a general-purpose, template-driven agent platform capable of safely composing agents that can reason about tasks and operate across local systems, development tools, infrastructure, data and external services.

## North-star architecture

`User → Orchestrator → Agent/Skill selection → MCP/Tool discovery → Policy → Sandbox → Execution → Verification → Memory/Audit`

## Initial MVP

The first runnable MVP should be intentionally narrow:

1. One agent runtime.
2. One model gateway interface with pluggable providers.
3. Filesystem tools limited to a workspace.
4. Git tools limited to a selected repository.
5. Bash/PowerShell execution through an approval-aware sandbox.
6. Docker read/inspect operations first; write/destructive operations gated.
7. MCP client and registry.
8. Skill manifests and loader.
9. Policy engine.
10. Structured event/audit log.

## Definition of Done for MVP

- An agent can inspect a repository.
- It can select a coding/debugging skill.
- It can discover the required tools through the capability registry.
- Every tool call is policy checked.
- Shell execution is isolated or explicitly approved.
- The agent can modify code and run tests.
- The agent can show a final diff and execution trace.
- No secret is printed to the model or logs unintentionally.

## Non-goals for MVP

- Fully autonomous production deployment.
- Unrestricted host administration.
- Automatic destructive system changes.
- A single universal prompt containing every tool.

## Engineering strategy

Build bottom-up contracts first, then adapters, then orchestration, then specialized agents. Keep all integrations replaceable so local models (for example Ollama) and hosted model gateways can coexist behind the same model interface.
