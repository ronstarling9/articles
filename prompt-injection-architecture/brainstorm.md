# Prompt Injection Architecture Article – Brainstorm

## Status
Design phase complete. Ready for drafting.

## Target Platform
LinkedIn post, 300-500 words

## Audience
Software engineering leaders whose teams are building LLM integrations. Technical enough to evaluate solutions, focused on decision-making rather than implementation details.

## Thesis
"The prompt injection problem isn't a filtering problem. It's an architecture problem."

Defense in depth is the only real answer—no single mitigation is sufficient.

## Hook
You can't regex your way past an adversary who can rephrase attacks in Swahili, pig latin, or base64. The real question is: when your filters fail—and they will—what can a hijacked LLM actually touch?

## Title Options
- "The Prompt Injection Problem Isn't a Filtering Problem. It's an Architecture Problem."
- "You Can't Filter Your Way to LLM Security"

## Article Arc

1. **Hook** (2-3 sentences) – Filtering doesn't work. Regex can't catch attacks in 100 languages.

2. **Reframe** (2-3 sentences) – The real question isn't "how do I sanitize input?" It's "what can a hijacked LLM touch?"

3. **Three Tiers** (~150-200 words) – Brief, conceptual—no code:

   **Tier 1: Architecture**
   - Deterministic orchestration – LLM is a function called by a deterministic system, not an agent with integration credentials. LLM never directly touches external systems (Jira, GitHub, etc.).
   - Least privilege per task – Tool permissions scoped per action type. Investigation doesn't need write access. Code review doesn't need network.

   **Tier 2: Containment**
   - Sandboxing – OS-level isolation (bubblewrap), restricted filesystem access, credential blocking (.env files)
   - Statelessness – Fresh environment per action, repo cloned new each time. No persistent foothold, no state to compromise.

   **Tier 3: Detection & Deflection**
   - Structured prompts – Clear boundaries between instructions and untrusted data (tagged data sections)
   - Task anchoring – Strong semantic intent makes off-task injections incongruous to the model
   - Monitoring – Permission denial logging, output structure validation, secrets scanning

4. **Close** – Call to action + engagement hook:
   - "Before your team ships that LLM integration, ask: what can it touch if it misbehaves?"
   - "What architectural patterns are you using to contain LLM risk?"

## Tone
Same contrarian, senior-consultant voice as the AI coding piece. Direct, no hedging.

## Source Material

### ALM Orchestrator Implementation
Reference: `~/repos/alm-orchestrator`

Key implementation details (for author reference, not for article):
- Sandbox settings per action type (`prompts/*.json`)
- Permission deny lists: Write, Edit, WebFetch, curl, wget, nc, ssh, .env files
- Format string injection protection (`_escape_format_string()`)
- `<jira_user_content>` tags with explicit "treat as DATA not instructions" framing
- Permission denial logging in `ClaudeExecutor`

### OWASP LLM Prompt Injection Prevention Cheat Sheet
https://cheatsheetseries.owasp.org/cheatsheets/LLM_Prompt_Injection_Prevention_Cheat_Sheet.html

Key mitigations referenced:
- Input validation and sanitization (article will argue this is insufficient alone)
- Structured prompts with clear separation
- Output monitoring and validation
- Agent-specific protections (tool validation, least privilege)
- Least privilege architecture
- Comprehensive monitoring

## Key Insight
The architectural insight: you're not trying to make the LLM "behave," you're limiting what a misbehaving LLM can do. Assume compromise, contain blast radius.

## Next Steps
- [ ] Draft the article (~300-500 words)
- [ ] Review with elements-of-style:writing-clearly-and-concisely skill
- [ ] Move to article.md when ready
