---
name: one-three-one-rule
description: "Use when choosing between multiple technical approaches — structure decisions as 1 problem → 3 options → 1 recommendation."
version: 1.0.0
author: Hermes Agent
license: MIT
metadata:
  hermes:
    tags: [decision-making, technical-choices, architecture]
    related_skills: [plan, spike]
---

# One-Three-One Decision Framework

## Overview

The One-Three-One Rule is a structured decision-making framework: articulate exactly **one problem**, propose exactly **three viable options**, and make exactly **one recommendation**.

This prevents:
- Analysis paralysis (infinite options)
- Premature narrowing (only 1-2 options considered)
- Decision without justification (no recommendation, just options)

## When to Use

- Choosing between frameworks, libraries, or architectures
- Deciding on a technical approach for a feature
- Resolving a disagreement about implementation strategy
- Any decision where you need to show your reasoning

Do NOT use for: trivial binary decisions (use/not-use), personal preferences, or when speed matters more than rigor.

## Structure

### 1. State the Problem (One)

Write one clear sentence defining what needs to be decided. Include constraints.

> **Problem:** Choose a web framework for our new SaaS dashboard. Constraints: TypeScript, real-time data, team already knows React.

### 2. Propose Options (Three)

For each option:
- **Name** the option
- **Brief description** (2-3 sentences)
- **Pros** (2-4 points)
- **Cons** (2-4 points)
- **Effort estimate** if relevant

### 3. Make a Recommendation (One)

State your recommendation clearly and justify it:

> **Recommendation:** Option B
> **Why:** [2-3 sentence justification tying back to the problem]
> **Tradeoff accepted:** [what you're giving up]

## Example

**Problem:** Choose a state management library for a React app with complex form state.

**Option A: Redux Toolkit**
- Pros: Industry standard, large ecosystem, devtools
- Cons: Boilerplate, steep learning curve, overkill for forms
- Effort: Medium

**Option B: Zustand**
- Pros: Minimal API, no boilerplate, works outside React
- Cons: Smaller ecosystem, no built-in devtools
- Effort: Low

**Option C: useReducer + Context**
- Pros: Zero dependencies, native React, simple
- Cons: No middleware, re-render issues at scale, no persistence
- Effort: Minimal

**Recommendation:** Option B — Zustand. The form state is moderate complexity; Zustand's minimal API avoids Redux overhead while providing the persistence and devtools hooks we need. The ecosystem gap is not relevant for this use case.

## Common Pitfalls

1. **False options** — Don't include a deliberately bad option just to fill the slot
2. **Straw man framing** — Describe each option fairly, not with leading language
3. **Missing recommendation** — Listing options without choosing one doesn't help
4. **Ignoring the problem** — Each option must be evaluated against the original problem, not in the abstract

## Verification Checklist

- [ ] Problem is one clear sentence
- [ ] Exactly three options listed with pros/cons
- [ ] One recommendation with explicit justification
- [ ] Recommendation ties back to the stated problem
