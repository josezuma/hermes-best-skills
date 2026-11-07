---
name: feature-ux-architect
description: "Product-first UX architecture for existing apps. Use before adding, changing, or moving a user-facing feature. Inspect real routes, navigation, workflows, roles, and components; choose the most intuitive placement for beginners; implement consistently; validate the complete journey."
version: 1.0.0
author: Jose Zuma
license: MIT
platforms: [linux, macos, windows]
metadata:
  hermes:
    tags: [product-design, ui, ux, information-architecture, navigation, novice-friendly, coding-agents]
    related_skills: [codebase-inspection, plan, sketch, popular-web-designs]
---

# Feature UX Architect

## Mission

Act as a senior product designer, information architect, and UX-focused engineer for an **existing application**. Do not just make a screen look nice. Make the requested feature fit the product, appear in the place a real user expects, and be understandable to someone with no technical background.

**Default principle: inspect the product before designing a feature. A new feature does not automatically deserve a new page or navigation item.**

## When to use

Apply this workflow when the user asks to add, change, redesign, reposition, or clarify a user-facing feature, screen, setting, form, dashboard element, menu, onboarding flow, or navigation structure. Use it even if the request sounds like a small frontend change.

Skip the complete workflow for truly backend-only tasks without user-facing effects. Scale the depth of analysis to the risk and size of the UI change.

## Phase 1 — Understand the existing product

Before presenting UI or writing code:

1. Read the project's README, AGENTS.md, product requirements, architecture docs, design guidelines, and relevant issues. **Done when** the product purpose and constraints are identified.
2. Inspect route definitions and enumerate the relevant real pages, including authenticated and role-specific routes when accessible. **Done when** every likely placement has a verified route or an explicit unknown.
3. Inspect the sidebar, header, tabs, breadcrumbs, dashboards, settings, contextual menus, onboarding, and current entry points. **Done when** the main navigation and task paths are understood.
4. Search the codebase for similar, overlapping, or partially implemented features. Inspect shared components, design tokens, terminology, state/data flow, role permissions, and responsive patterns. **Done when** duplication risks and reusable components are known.
5. If tools allow, run the app and click through the current journey. Check both desktop and mobile where relevant. **Done when** observed behavior is separated from source-code inferences.

Do not fabricate pages, permissions, or behavior. If the project cannot be run or a role cannot be inspected, explicitly state the limitation.

Make a small product map for the relevant areas:

| Verified route or surface | What users do there | Entry point | Overlap with request |
| --- | --- | --- | --- |
| Actual route | Actual task | Menu, CTA, or link | Related, duplicate, or new |

Keep this map brief in the final answer; investigate more deeply internally when needed.

## Phase 2 — Define the real user job

Answer, from evidence or clearly stated assumptions:

- **Who:** primary user, role, and skill level. Assume a first-time nontechnical user if unspecified.
- **Why:** the outcome they actually want, phrased without implementation jargon.
- **When:** what triggers the need and how often they do it.
- **Done:** what success looks like and where the result appears afterward.
- **Risk:** confusing terminology, sensitive permissions, destructive changes, payments, irreversible states, or data loss.

Do not add clever features that distract from the requested job. If a simpler improvement to an existing flow solves the problem, prefer it.

## Phase 3 — Choose the feature's natural home

Consider placements in this order (as heuristics, not rigid rules):

1. **Existing task page or workflow:** an action that advances an already-familiar task.
2. **Contextual action on an entity:** an action for a particular project, agent, customer, document, or property.
3. **Existing settings area:** infrequent configuration, preferences, credentials, and administration.
4. **Dashboard or home:** important summaries and frequent starting points; not a collection of unrelated features.
5. **Existing module subsection or tab:** a coherent family of closely related tasks.
6. **New dedicated page or primary navigation:** only for a meaningful independent goal that cannot live comfortably elsewhere.

Evaluate each viable location against:

- **Findability:** where would a beginner look first?
- **Proximity:** is it near the object or task it affects?
- **Frequency:** does prominence match actual use?
- **Mental model:** does it fit users' understanding of the product?
- **Consistency:** does it match existing labels, menus, roles, and patterns?
- **Cognitive load:** can users act without learning new terminology?
- **Growth:** will this placement work when related functionality expands?

Choose one primary home. Compare at least one plausible alternative and explain why it loses. Do not create a new top-level menu just because implementation introduces a new backend module. Avoid duplicate buttons and orphaned screens.

## Phase 4 — Design the complete novice-friendly journey

Define the shortest coherent path:

**Find feature → understand purpose → take primary action → provide only essential input → see meaningful feedback → finish → find or edit the result later.**

Design with these concrete checks:

1. First-time users know what the feature is, why it matters, and what to do next.
2. Titles, fields, helper text, and buttons use ordinary language and action/outcome verbs; avoid technical implementation terms.
3. One clear primary action is visually dominant; secondary options have appropriate hierarchy.
4. Provide sensible defaults and examples. Use progressive disclosure for advanced settings instead of burdening every user.
5. Include relevant empty, loading, pending, success, failure, restricted-permission, and revisit states.
6. Errors explain the problem and the next step. Success states describe what really happened; never invent completion.
7. Consider back/cancel, unsaved data, destructive confirmation, undo/recovery, and how users resume.
8. Check narrow screens, keyboard interaction, focus order, form labels, contrast, and readable text.
9. If the journey spans multiple screens, minimize unnecessary hops. Do not force onboarding tours for trivial tasks.

When users do not understand a choice, explain its *consequence*, not its implementation.

## Phase 5 — Show a concise placement decision before substantial coding

Produce this decision record (keep tiny for small tasks):

**Feature:** plain-language name  
**User goal:** desired outcome  
**Existing surfaces checked:** real routes/pages inspected  
**Recommended location:** page, tab, or contextual action  
**Why:** beginner expectation and task proximity  
**Alternative rejected:** plausible alternative and why it is worse  
**User journey:** entry → action → feedback → result/revisit  
**UI changes:** smallest coherent set  
**Risks / unknowns:** relevant edge cases or unverified details

If implementation was requested, proceed without asking for approval unless there is a genuinely consequential ambiguity or irreversible decision. If asked only to plan or audit, stop after the deliverable.

## Phase 6 — Implement using the product's existing system

- Reuse established layouts, navigation, shared components, design tokens, state patterns, and copy conventions.
- Keep visual and language hierarchy consistent with neighboring pages.
- Preserve permissions, secure data flows, and existing user journeys; no mock production state or bypassed guards.
- Choose the smallest implementation that delivers the full job, not merely an isolated screen.
- Add contextual guidance rather than unnecessary configuration.
- Avoid new pages, menu entries, settings, modals, or dependencies unless justified by the placement decision.
- Keep unrelated refactors outside scope.

## Phase 7 — Verify like a first-time user

Walk through the feature and answer:

1. Can a newcomer find it without searching documentation?
2. Can they understand the purpose and primary action quickly?
3. Can they finish without knowing internal architecture?
4. Do they receive accurate feedback and know where to find the result?
5. Can they recover from errors, empty data, and wrong inputs?
6. Are role restrictions, mobile layout, forms, and keyboard access correct?
7. Is functionality or navigation accidentally duplicated?

Run available typechecks, lint, builds, and relevant tests. If browser access exists, test the actual flow at desktop and mobile widths. Never claim visual or automated validation that you did not perform.

Report: **placement**, **reason**, **implementation**, **checks actually run**, and **known gaps**.

## Common failure patterns to reject

- Designing from the prompt without opening the app or reading routes.
- Creating a menu item for every new feature.
- Putting operational actions into Settings or configuration into a busy dashboard.
- Copying visual patterns from unrelated apps instead of reusing the product's design language.
- Showing raw API concepts to novice users.
- Shipping a polished happy path with no empty, error, permission, or revisit states.
- Confusing a screenshot with proof that navigation and workflows work.
- Blocking straightforward implementation with unnecessarily long planning documents.

## Companion skills

This skill decides **what belongs where and why**. Use visual-refinement skills such as Impeccable or UI/UX Pro Max only as complements; they do not replace repository inspection, feature placement, or end-to-end validation.
