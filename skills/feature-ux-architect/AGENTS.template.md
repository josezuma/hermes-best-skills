# Product-first UI/UX rules for coding agents

Apply these rules whenever designing or implementing a user-facing feature in this project.

1. **Inspect first.** Read the product docs and real route definitions. Check the current sidebar, pages, navigation, settings, roles, related features, components, and design tokens before deciding on UI.
2. **Follow the skill.** Read .agents/skills/feature-ux-architect/SKILL.md when available. If your agent's skills live elsewhere, load the installed feature-ux-architect skill explicitly.
3. **Design for beginners.** A first-time nontechnical user should understand where to go, what to do, what happens next, and how to recover from mistakes.
4. **Choose a natural location.** Prefer the existing relevant workflow or contextual action; do not add new pages or top-level menu entries without a strong user-centered reason.
5. **Avoid duplicates.** Check for overlapping features, fragmented settings, redundant navigation, or multiple places to perform the same task.
6. **Reuse conventions.** Follow the app's existing components, labels, spacing, design tokens, permissions, and responsive behavior.
7. **Plan the full journey.** Consider entry, orientation, action, success, revisit, loading, empty states, errors, cancellation, and role restrictions as applicable.
8. **Explain the placement briefly.** Before a substantial UI change, state where the feature should live, why, one rejected alternative, and the main user journey. Continue implementation when asked.
9. **Validate honestly.** Run relevant checks and browser tests when available; state anything not verified.

Do not replace or discard other rules in an existing AGENTS.md. Merge these instructions into it.
