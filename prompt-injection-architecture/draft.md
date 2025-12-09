# The Prompt Injection Problem Isn't a Filtering Problem. It's an Architecture Problem.

I've been building LLM integrations into the software development lifecycle—automated code review, ticket triage, investigation workflows. The productivity gains are real. So is the security exposure. These systems ingest untrusted content from Jira tickets, pull requests, and user comments, then act on it. Prompt injection isn't theoretical here; it's the primary threat model.

You can't regex your way past an adversary who can rephrase attacks in Swahili, українська, pig latin, or base64. [Practitioners already know](https://cheatsheetseries.owasp.org/cheatsheets/LLM_Prompt_Injection_Prevention_Cheat_Sheet.html#best-of-n-attack-mitigation): content filters and safety training can be systematically defeated. The real question isn't "how do I sanitize input?" It's "what can a hijacked LLM actually touch?"

Assume your filters will fail. Then build accordingly. There are three dimensions I consider: architecture, containment, and detection.

## Architecture

The LLM is a function called by a deterministic orchestrator—not an agent with integration credentials. The orchestrator follows hardwired logic that cannot change at runtime. It controls integrations with systems of record like Jira and GitHub, fetches the data, and provides the LLM with everything it needs to perform a task. The model analyzes and generates; it never directly touches external systems.

Permissions get scoped per task. An investigation workflow doesn't need write access. A code review task doesn't need network. If the LLM gets hijacked, the blast radius is limited to what that specific task was allowed to do in the first place.

## Containment

The LLM runs inside an OS-level sandbox—a container or namespace with its own restricted view of the filesystem and network. Only allowlisted paths are visible. Outbound network access can be disabled entirely or limited to specific endpoints. The model can't reach what it can't see.

Each action runs in a fresh environment. The repo gets cloned new; there's no persistent state between invocations. A compromised prompt can't establish a foothold because there's nothing to persist to. When the task ends, the environment is destroyed.

## Detection

Structured prompts draw clear boundaries between instructions and untrusted data. Tags and delimiters mark external content explicitly, making it harder for injections to masquerade as system instructions.

Task anchoring takes this further. When the model has a clear, specific purpose—"analyze this code for security vulnerabilities"—injections that try to redirect it toward unrelated actions become semantically incongruous. The model is primed to stay on task, and off-topic instructions feel out of place. It's not foolproof, but it raises the bar.

Monitoring closes the loop. Requiring structured JSON output with a defined schema per task type makes validation straightforward—you can check field types, required keys, and value constraints before acting on anything the model returns. Permission denials get logged so you can see what the model tried to do. Secrets scanners catch credential leaks before they leave the system. None of this prevents attacks, but it shortens your detection window.

## The Point

No single layer is sufficient. Filters help but fail. Sandboxes contain but can be escaped. Monitoring detects but doesn't prevent. Stack them.

Before your team ships that LLM integration, ask: what can it touch if it misbehaves?

What architectural patterns are you using to contain LLM risk?
