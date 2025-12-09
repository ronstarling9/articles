# The Prompt Injection Problem Isn't a Filtering Problem. It's an Architecture Problem.

You can't regex your way past an adversary who can rephrase attacks in Swahili, pig latin, or base64. Research confirms what practitioners already know: content filters and safety training can be systematically defeated. The real question isn't "how do I sanitize input?" It's "what can a hijacked LLM actually touch?"

Assume your filters will fail. Then build accordingly.

## Tier 1: Architecture

The LLM is a function called by a deterministic orchestrator—not an agent with integration credentials. It never directly touches Jira, GitHub, or your database. Every external action routes through code you control, with permissions scoped per task. Investigation doesn't need write access. Code review doesn't need network.

## Tier 2: Containment

OS-level sandboxing restricts filesystem access and blocks credential files. Each action runs in a fresh environment—repo cloned new, no persistent state. A compromised prompt can't establish a foothold because there's nothing to persist to.

## Tier 3: Detection

Structured prompts draw clear boundaries between instructions and untrusted data. Strong task anchoring makes off-topic injections semantically incongruous. Permission denials get logged. Outputs get validated. Secrets get scanned.

## The Point

No single layer is sufficient. Filters help but fail. Sandboxes contain but can be escaped. Monitoring detects but doesn't prevent. Stack them.

Before your team ships that LLM integration, ask: what can it touch if it misbehaves?

What architectural patterns are you using to contain LLM risk?
