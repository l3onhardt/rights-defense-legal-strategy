# Team Mode

Use team mode to make the work resemble a disciplined legal operations team. Do not use it for every question. Use it when parallel research, adversarial modeling, or independent review materially improves accuracy or strategy.

The team must not become a group of yes-men. At least one role should attack the user's plan or assumptions when the matter is contested.

## Table of Contents

1. Trigger Team Mode
2. Main Agent Role
3. Recommended Subagents
4. Delegation Rules
5. Reconciliation Rules
6. Case Dossier
7. Example Subagent Prompts

## 1. Trigger Team Mode

Consider team mode when at least one is true:

- The matter has multiple legal issues, multiple parties, or cross-domain facts.
- The user faces a lawyer letter, corporate legal department, platform enforcement, administrative process, arbitration, lawsuit, criminal risk, or major negotiation.
- Money, business continuity, account control, employment, housing, public reputation, personal safety, or administrative/criminal consequences are meaningful.
- Current law, local procedure, platform rules, similar cases, opponent behavior, and forum power all matter.
- The user asks for deep strategy, adversarial modeling, “杀死比赛”, or a plan that must survive pushback.

Do not use team mode for simple wording, basic evidence sorting, or low-stakes questions where the main agent can verify directly.

## 2. Main Agent Role

The main agent is the case lead. It must:

1. Intake facts and define the user's goal and fallback goals.
2. Frame narrow issues before delegation.
3. Decide which streams are independent.
4. Give each subagent facts, jurisdiction, forum, user goal, and required output format.
5. Avoid duplicating work across subagents.
6. Reconcile conflicts, source quality, and strategic tradeoffs.
7. Produce the final user-facing action plan.

Never outsource final judgment. Subagent outputs are research, attack surfaces, and review inputs, not final advice.

## 3. Recommended Subagents

### Law Researcher

Purpose: verify current law, regulations, judicial interpretations, local procedures, and platform rules for identified issues.

Use when: legal basis, deadlines, jurisdiction, complaint route, authority, or procedure affects the strategy.

Required output:

```text
issue:
verified source:
official url or source name:
effective/amendment date:
rule summary:
applies if:
does not apply if:
uncertainty/local variation:
strategic impact:
```

### Procedure and Channel Researcher

Purpose: identify filing channels, complaint portals, local court/arbitration requirements, evidence submission format, deadlines, responsible institutions, and rejection risks.

Required output:

```text
channel:
responsible institution:
scope/power level:
can grant or only pressure:
required materials:
deadline:
submission method:
expected response:
common rejection reasons:
```

### Case and Pattern Researcher

Purpose: find similar cases, regulator actions, platform precedents, public disputes, or court reasoning patterns.

Use when: practical outcomes, proof standards, settlement leverage, or regulator/court/platform attitude matters.

Required output:

```text
pattern:
sources found:
similarity to user's facts:
key differences:
outcome or handling:
useful lesson:
reliability:
```

### Opposing Counsel / Counterparty Modeler

Purpose: argue the opponent's strongest lawful position and predict their next moves.

Use when: the plan may face denial, delay, counterclaim, corporate legal response, landlord/employer/platform defense, or reputation attack.

Required output:

```text
opponent's strongest factual story:
opponent's strongest legal/contractual/platform defense:
opponent's strongest procedural defense:
evidence they may have:
weak points in user's story:
likely delay tactic:
likely counter-demand/counterclaim:
settlement posture:
what would make them comply:
```

### Decision-Maker Modeler

Purpose: model how the relevant judge, arbitrator, regulator, platform reviewer, mediator, police officer, administrative body, employer, or public audience would evaluate the matter.

Required output:

```text
decision-maker/forum:
scope and power:
main questions they will ask:
evidence they will value:
evidence/noise they may ignore:
common rejection reasons:
realistic remedy:
time/cost/enforcement reality:
credibility advice:
```

### Evidence Skeptic

Purpose: attack the current evidence record and identify the cheapest proof improvements.

Required output:

```text
facts currently proven:
facts only alleged:
facts likely disputed:
missing originals/metadata:
chain-of-custody or authenticity risks:
admission/waiver risks in prior messages:
cheapest proof-building action:
```

### Settlement Designer

Purpose: design terms that protect the user while giving the opponent a rational exit.

Required output:

```text
settlement objectives:
minimum acceptable terms:
valuable non-money terms:
release scope:
confidentiality/non-disparagement:
default clause:
performance verification:
risks of signing:
```

### Strategy Reviewer

Purpose: stress-test the main agent's planned countermeasures for legality, leverage, cost, evidence, escalation, unintended consequences, and remedy realism.

Required output:

```text
strong points:
weak points:
legal/procedural risks:
evidence risks:
negotiation risks:
retaliation/reputation risks:
remedy realism:
suggested safer alternative:
questions to ask user:
```

## 4. Delegation Rules

- Delegate only after the main agent has a short issue list. Do not ask subagents to “research everything.”
- Give subagents only the facts needed for their stream.
- Ask subagents to separate verified sources from inference.
- Require source names and dates for legal claims.
- Use official or authoritative sources first; unofficial summaries are clues only.
- Require opponent-modeling roles to make the user's case uncomfortable, not flattering.
- If a subagent cannot verify a point, mark it unverified instead of filling the gap with memory.

## 5. Reconciliation Rules

The main agent must reconcile:

```text
which facts are proven versus disputed:
which sources are strongest:
which route can actually grant the remedy:
which opponent defense is most dangerous:
which user demand should be narrowed or changed:
whether decisive leverage exists:
what second move follows each likely opponent response:
```

If subagents disagree, present the conflict and explain which source or practical assumption is stronger.

## 6. Case Dossier

For complex matters, keep a lightweight dossier in the answer or a local file only if the user asks.

Recommended sections:

```text
facts:
timeline:
evidence inventory:
issues:
verified authorities:
claim/defense/proof matrix:
opponent model:
decision-maker model:
similar cases/patterns:
channels and deadlines:
strategy options:
drafts sent:
settlement posture:
open questions:
```

Do not crawl and store all laws. Store only issue-relevant sources, extracts, links, and dates. Re-verify decisive legal authorities on each new matter or when time has passed.

## 7. Example Subagent Prompts

Law Researcher:

```text
Use $rights-defense-legal-strategy as a law researcher. Facts: [brief verified facts]. Jurisdiction/forum: [place/forum]. User goal: [goal]. Research only these issues: [issues]. Verify current mainland China legal/procedural/platform sources. Return the Law Researcher output format. Do not give final strategy.
```

Opposing Counsel / Counterparty Modeler:

```text
Use $rights-defense-legal-strategy as opposing counsel/counterparty modeler. Facts: [brief facts]. User goal: [goal]. Assume the opponent is competent and wants to minimize liability/cost. Build their strongest factual, legal, contractual/platform, procedural, and negotiation response. Identify the user's weakest points and likely opponent next moves. Do not flatter the user's position.
```

Decision-Maker Modeler:

```text
Use $rights-defense-legal-strategy as decision-maker modeler. Facts: [brief facts]. Proposed forum/channel: [forum]. Model how this judge/arbitrator/regulator/platform reviewer/mediator/police/admin body would evaluate jurisdiction, evidence, remedy, credibility, timing, and rejection reasons. Return realistic remedy and bottlenecks.
```

Evidence Skeptic:

```text
Use $rights-defense-legal-strategy as evidence skeptic. Facts and evidence: [summary]. Identify which facts are proven, alleged, likely disputed, or unsupported. Attack authenticity, completeness, chain-of-custody, admission, waiver, and missing-original risks. Return the cheapest proof-building actions.
```

Strategy Reviewer:

```text
Use $rights-defense-legal-strategy as strategy reviewer. Facts: [brief facts]. Draft plan: [plan]. Stress-test legality, evidence, opponent response, decision-maker view, settlement, remedy realism, and unintended consequences. Return risks and safer alternatives. Do not rewrite the final answer.
```
