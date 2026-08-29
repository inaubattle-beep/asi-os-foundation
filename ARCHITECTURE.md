# ASI OS Architecture

## 1. Mission

ASI OS is a modular agentic operating layer that composes LLM reasoning with skills, tools, MCP interfaces, memory, policy and external systems. The objective is not to create one giant agent with every permission; it is to create a controlled capability fabric from which specialized agents can be assembled dynamically.

## 2. Relational Model

```text
USER
  │
  ▼
AGENT ORCHESTRATOR ───────────────► EXTERNAL AI / SERVICES
  │                                  (LLM providers, APIs, SaaS)
  ├── Planning & Reasoning
  ├── Context / Memory
  ├── Skill Selection
  ├── Tool Selection & Execution
  └── Result Synthesis
  │
  ▼
SKILLS LAYER
  │   Coding · Debugging · DevOps · Network · Security · Data/DB · Research · System
  │
  ▼
MCP LAYER
  │   Filesystem · Git · GitHub · GitLab · Docker · Shell · Network · DB · Cloud · Browser
  │
  ▼
TOOL REGISTRY
  │   read_file · write_file · search · bash_exec · ps_exec · git_commit · git_push
  │   docker_run · http_request · ssh_exec · sql_query · ...
  │
  ▼
SYSTEMS & RESOURCES
      Filesystem · OS/Shell · Development · Git · GitHub · GitLab · Docker · Network
      Databases · Cloud/Infrastructure · Communication · Browsers · Other integrations

Governance & Safety cuts across every execution path:
Policy → Permissions → Sandbox/Isolation → Audit/Logging → Approval/Human-in-the-loop

Memory & Knowledge is available to planning, skill selection and result synthesis:
Short-term context → Long-term state → Vector/RAG → Cache

Templates & Agent Factory generate and compose Agents, Skills, Tools and MCP servers.
```

## 3. Responsibility Boundaries

| Layer | Responsibility |
|---|---|
| LLM | Reasoning, generation, interpretation and planning assistance |
| Agent Runtime | State machine, execution loop, context, retries and lifecycle |
| Orchestrator | Decompose goals and coordinate agents/capabilities |
| Skill | Describe a reusable method/workflow for a domain |
| Tool | Perform one concrete operation with a typed schema |
| MCP Server | Expose tools/resources through a standardized protocol boundary |
| Tool Registry | Discover capabilities, schemas, risk and requirements |
| Policy Engine | Decide whether an operation is allowed |
| Sandbox | Restrict execution and blast radius |
| Memory | Persist useful state/knowledge and retrieve context |
| Agent Factory | Instantiate agents from templates |

## 4. Execution Flow

1. Receive user intent.
2. Normalize the task and identify constraints.
3. Retrieve relevant memory and project context.
4. Select or synthesize an agent template.
5. Select required skills.
6. Discover MCP servers and tools.
7. Select the smallest useful set of tools.
8. Run policy and permission checks.
9. Request human approval when required.
10. Execute inside the appropriate isolation boundary.
11. Validate output with tests/checks.
12. Return a structured result.
13. Store useful state in memory and audit the execution.

## 5. Capability Discovery

The runtime should load capabilities on demand instead of placing every tool definition into every context window. Each capability should advertise:

- stable ID and version
- description
- input/output schema
- required permissions
- risk level
- authentication requirements
- execution environment
- dependencies
- health status
- audit metadata

## 6. Security Principles

- Default deny for sensitive operations.
- Least privilege per agent/task.
- Workspace-scoped filesystem access by default.
- Allowlisted commands where feasible.
- Network egress controls.
- Secrets never injected into model context unless explicitly required.
- Production deployment and destructive operations require approval.
- Full tool-call audit trail.
- Timeouts, quotas and cancellation.
- Isolation for untrusted code.

## 7. Target Integrations

### Local/system
Filesystem, Bash, PowerShell, CMD, Python, SSH, process management, package managers, compilers, debuggers and test runners.

### Development
Git, GitHub, GitLab, CI/CD, Docker, Kubernetes, Terraform, package registries and code hosting services.

### Network
DNS, HTTP, TCP, ping, traceroute, SSH, interface inspection, routing diagnostics, VPNs and network-device APIs.

### Data
PostgreSQL, MySQL, SQLite, Redis, MongoDB, object storage and vector databases.

### Cloud
AWS, Azure, GCP, Vercel, Cloudflare and other provider APIs.

### Human/communication
Slack, email, Telegram, Discord and webhook-based systems.

## 8. Design Rule

The system should remain composable:

`Agent = Template + Skills + MCP capabilities + Tools + Memory + Policy`

and not:

`Agent = one prompt + unrestricted operating-system access`.
