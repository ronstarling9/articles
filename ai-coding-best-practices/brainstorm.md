# AI Coding Best Practices Article - Brainstorm Notes

## Article Overview

**Title:** AI Won't Fix Your Broken Engineering Culture. It'll Expose It.

**Target Platform:** LinkedIn post (300-400 words)

**Target Audience:** Technology professionals, consultants, PE operating partners

**Author Voice:** Ron Starling - Senior consultant at EY-Parthenon with experience transforming software engineering organizations

## Goals

1. **Establish thought leadership** - Position as authority on AI coding adoption
2. **Gather data** - Use comments as informal research to validate/refine hypothesis

## Strategic Choices

- **Tone:** Deliberately contrarian - "Everyone's excited about AI coding, but here's the uncomfortable truth"
- **Framing:** "The Amplifier" - AI tools amplify what you already have; good practices become great, bad practices become catastrophic
- **Structure:** Question-based - Lead with questions that invite reflection and response
- **Evidence:** Analytical with research citations, but not academic - enough to be credible

## Core Hypothesis

Companies with mature processes (CMMI level 3+) and best practices (TDD, disciplined defect tracking, documented coding standards) will experience higher sustained productivity gains from AI coding tools. Those without will see modest initial gains but then find themselves mired in more technical debt.

## Key Messages

1. "What did your engineering practices look like before?" is the right question
2. AI coding tools are amplifiers - they supercharge whatever you already have
3. Initial velocity gains often dissipate while technical debt persists
4. Most organizations lack the instrumentation to even measure whether they're improving
5. TDD, requirements discipline, and coding standards are guardrails, not bureaucracy

---

## Research Summary

### METR Study (2025)
- **Source:** https://metr.org/blog/2025-07-10-early-2025-ai-experienced-os-dev-study/
- **Finding:** Experienced developers were 19% SLOWER with AI tools
- **Key insight:** Developers who knew their codebases and had rigorous practices could direct AI effectively; those who didn't spent more time fixing mistakes

### Cursor Adoption Study (Academic - arxiv)
- **Source:** https://arxiv.org/html/2511.04427
- **Finding:** 3-5x velocity gains in first month, but gains dissipate after two months
- **Technical debt accumulation:**
  - Static analysis warnings increased 30%
  - Code complexity increased 41%
- **Key insight:** "Self-reinforcing cycle where initial productivity surges give way to maintenance burdens"

### DORA Report (2024)
- **Finding:** 25% increase in AI adoption → only 2.1% productivity boost
- **Trade-off:** Delivery stability DECREASES 7.2%, throughput drops 1.5%

### Multi-Company Study (Microsoft, Accenture, Fortune 100)
- **Source:** https://itrevolution.com/articles/new-research-reveals-ai-coding-assistants-boost-developer-productivity-by-26-what-it-leaders-need-to-know/
- **Overall finding:** 26% average productivity increase
- **Junior vs Senior gap:**
  - Junior developers: 27-39% gains
  - Senior developers: 8-13% gains
- **Implication:** Process maturity and codebase knowledge matter

### The Productivity Paradox
- **Source:** https://www.faros.ai/blog/ai-software-engineering
- **Finding:** 75% of engineers use AI tools, yet most organizations see no measurable performance gains
- **Range:** Results vary wildly from 26% faster to 19% slower

### Anthropic's Official Guidance
- **Source:** https://www.anthropic.com/engineering/claude-code-best-practices
- **Key recommendation:** TDD is essential for agentic coding
- **Quote:** "Test-driven development becomes even more powerful with agentic coding"

### Code Quality Trends (GitClear data)
- Code reuse ("moved" code) dropped from 25% (2021) to <10% (2024)
- Duplicate code blocks increased 10x in two years
- Defect rates grew 4x in AI-assisted code

### Maturity Curve Insight
- **Source:** https://lanternstudios.com/insights/blog/the-future-is-agentic-your-complete-guide-to-ai-powered-software-engineering/
- **Quote:** "The most common mistake organizations make is choosing the pathway they want to be on rather than matching their current reality"

---

## Final Article Draft

**AI Won't Fix Your Broken Engineering Culture. It'll Expose It.**

Everyone's asking: "What productivity gains are you seeing from AI coding tools?"

But that's the wrong question.

The right question: What did your engineering practices look like *before* you adopted these tools?

After years of transforming software engineering organizations and watching dozens of SaaS companies adopt agentic AI, I'll make a prediction: The gap between disciplined and undisciplined engineering teams is about to become a chasm.

AI coding tools are amplifiers. Companies with mature practices—test-driven development, disciplined defect tracking, documented coding standards—will see those practices supercharged. Companies without them will generate code faster than ever. And technical debt faster than ever.

The research backs this up. A [recent study of Cursor adoption](https://arxiv.org/html/2511.04427) found initial velocity gains of 3-5x—but those gains dissipated within two months. What persisted? A 30% increase in static analysis warnings and 41% jump in code complexity.

Meanwhile, [METR's 2025 study](https://metr.org/blog/2025-07-10-early-2025-ai-experienced-os-dev-study/) found that *experienced* developers were actually 19% slower with AI tools. The difference? Context and discipline. Developers who knew their codebases and had rigorous practices could direct the AI effectively. Those who didn't spent more time fixing AI-generated mistakes than they saved.

This isn't a tool problem. It's a process problem.

And here's the uncomfortable question most leaders can't answer: How do you *know* your engineering department is actually improving? Not just shipping faster—but shipping better? Most software organizations lack the basic instrumentation to measure. If you can't track defect escape rates, cycle time, or rework percentages today, AI adoption won't give you visibility. It'll just give you faster chaos.

TDD, clear requirements, documented standards—these aren't bureaucratic overhead. They're the guardrails that keep AI productivity real instead of illusory. Even [Anthropic's own engineering guidance](https://www.anthropic.com/engineering/claude-code-best-practices) for Claude Code emphasizes test-driven development as essential.

So I'm curious: What's your experience?

Are you seeing sustained productivity gains from AI coding tools—or an initial spike that's quietly creating cleanup work? And be honest: do you have the metrics to actually know the difference?

---

**Word count:** ~370 words

## Future Refinement Ideas

- Could add specific client examples (anonymized) if more concreteness needed
- Could split into a series: Part 1 on the amplifier effect, Part 2 on measurement gaps
- Could develop a "readiness checklist" as follow-up content
- Consider cross-posting to Substack or Medium for longer-form version with full research citations
