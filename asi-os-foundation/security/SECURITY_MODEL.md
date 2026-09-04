# Security Model

The security plane is a mandatory cross-cutting layer.

## Control sequence

`Request → Policy → Permission → Approval (if required) → Sandbox → Tool → Audit`

## Default posture

- Deny sensitive capabilities unless explicitly granted.
- Scope filesystem access to a workspace.
- Prefer command allowlists for shell tools.
- Restrict network egress by policy.
- Separate development and production credentials.
- Require approval for destructive or production actions.
- Log identity, task, tool, arguments metadata, decision, result and timestamp.
