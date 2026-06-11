# Team Mode

Use team mode to make the work resemble a disciplined legal operations team. Do not use it for every question. Use it when parallel research materially improves accuracy or speed.

## Trigger Team Mode

Consider team mode when at least one is true:

- The matter has multiple legal issues, multiple parties, or cross-domain facts.
- The user faces a lawyer letter, corporate legal department, platform enforcement, administrative process, arbitration, lawsuit, criminal risk, or major negotiation.
- Money, business continuity, account control, employment, housing, public reputation, personal safety, or administrative/criminal consequences are meaningful.
- Current law, local procedure, platform rules, and similar cases all matter.
- The user asks for a deep strategy, not a quick answer.

Do not use team mode for simple wording, basic evidence sorting, or low-stakes questions where the main agent can verify directly.

## Main Agent Role

The main agent is the case lead. It must:

1. Intake facts and define the user's goal.
2. Frame the issues before delegation.
3. Decide which research streams are independent.
4. Give each subagent narrow instructions and required output format.
5. Avoid duplicating work across subagents.
6. Reconcile conflicts and gaps.
7. Produce the final user-facing action plan.

Never outsource final judgment. Subagent outputs are evidence and analysis, not final advice.

## Recommended Subagents

### Law Researcher

Purpose: verify current law, regulations, judicial interpretations, local procedures, and platform rules for identified issues.

Use when: legal basis, deadlines, jurisdiction, complaint route, authority, or procedure affects the strategy.

Required output:

```text
Issue:
Verified source:
Official URL or source name:
Effective/amendment date:
Rule summary:
Applies if:
Does not apply if:
Uncertainty/local variation:
Strategic impact:
```

### Case and Pattern Researcher

Purpose: find similar cases, regulator actions, platform precedents, public disputes, or court reasoning patterns.

Use when: practical outcomes, proof standards, settlement leverage, or regulator/court attitude matters.

Required output:

```text
Pattern:
Sources found:
Similarity to user's facts:
Key differences:
Outcome or handling:
Useful lesson:
Reliability:
```

### Procedure and Channel Researcher

Purpose: identify filing channels, complaint portals, local court/arbitration requirements, evidence submission format, deadlines, and responsible institutions.

Use when: the next step depends on where/how to file or complain.

Required output:

```text
Channel:
Responsible institution:
Scope:
Required materials:
Deadline:
Submission method:
Expected response:
Risks or common rejection reasons:
```

### Strategy Reviewer

Purpose: stress-test the main agent's planned countermeasures for legality, leverage, cost, and unintended consequences.

Use when: the plan involves escalation, public communication, settlement, admission, reporting to authorities, or litigation/arbitration.

Required output:

```text
Strong points:
Weak points:
Legal/procedural risks:
Evidence risks:
Negotiation risks:
Suggested safer alternative:
Questions to ask user:
```

## Delegation Rules

- Delegate only after the main agent has a short issue list. Do not ask subagents to "research everything."
- Give subagents facts, jurisdiction, parties, goal, and issue scope. Do not pass irrelevant private material.
- Ask subagents to separate verified sources from inference.
- Require source names and dates for legal claims.
- Use official or authoritative sources first; unofficial summaries are clues only.
- If subagents disagree, present the conflict and explain which source is stronger.
- If a subagent cannot verify a point, mark it unverified instead of filling the gap with memory.

## Case Dossier

For complex matters, keep a lightweight dossier in the answer or a local file only if the user asks. Recommended sections:

```text
Facts:
Timeline:
Evidence inventory:
Issues:
Verified authorities:
Similar cases/patterns:
Channels and deadlines:
Strategy options:
Drafts sent:
Open questions:
```

Do not crawl and store all laws. Store only issue-relevant sources, extracts, links, and dates. Re-verify decisive legal authorities on each new matter or when time has passed.

## Example Subagent Prompts

Law Researcher:

```text
Use $rights-defense-legal-strategy as a law researcher. Facts: replace this with the brief verified facts. Jurisdiction: replace this with the place or forum. User goal: replace this with the desired outcome. Research only these issues: replace this with the framed issues. Verify current mainland China legal/procedural sources. Return the required Law Researcher output format. Do not give final strategy.
```

Case and Pattern Researcher:

```text
Use $rights-defense-legal-strategy as a case and pattern researcher. Facts: replace this with the brief verified facts. Search for similar cases, regulator actions, platform precedents, or public handling patterns. Return similarities, differences, outcomes, reliability, and practical lessons. Do not give final strategy.
```

Strategy Reviewer:

```text
Use $rights-defense-legal-strategy as a strategy reviewer. Facts: replace this with the brief verified facts. Draft plan to review: replace this with the current proposed plan. Stress-test legality, evidence, negotiation, escalation, and unintended consequences. Return risks and safer alternatives. Do not rewrite the final answer.
```
