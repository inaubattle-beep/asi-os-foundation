# ASI OS Relationship Map

## Conceptual relationships

```text
                         ┌───────────────┐
                         │      LLM      │
                         │ reasoning     │
                         └───────┬───────┘
                                 │
                                 ▼
                      ┌────────────────────┐
                      │  AGENT RUNTIME     │
                      │ state + execution  │
                      └─────────┬──────────┘
                                │
                    ┌───────────┼───────────┐
                    ▼           ▼           ▼
                 Memory      Skills      Policies
                    │           │           │
                    │           ▼           ▼
                    │      MCP Discovery  Permissions
                    │           │           │
                    │           ▼           ▼
                    │      Tool Registry → Sandbox
                    │           │           │
                    └───────────┼───────────┘
                                ▼
                          Tool Execution
                                │
              ┌─────────────────┼─────────────────┐
              ▼                 ▼                 ▼
          Files/Code        Git/GitHub        Docker/Network
              │                 │                 │
              └─────────────────┼─────────────────┘
                                ▼
                         External Systems
                                │
                                ▼
                         Result / Events
                                │
                    ┌───────────┴───────────┐
                    ▼                       ▼
                 Memory                  Audit
                    │
                    └──────► Next Decision
```

## Vocabulary

- **LLM:** reasoning/generation engine.
- **Agent:** an execution identity composed from capabilities and policies.
- **Skill:** reusable domain procedure and behavioral contract.
- **Tool:** atomic action.
- **MCP:** interoperability boundary for tools/resources.
- **Resource:** information exposed to an agent without necessarily performing an action.
- **Memory:** retrievable task state and knowledge.
- **Policy:** authorization decision.
- **Sandbox:** constrained execution environment.
