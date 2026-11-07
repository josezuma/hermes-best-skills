# Feature UX Architect

A reusable **product-first UI/UX skill for coding agents**. Before implementing a requested feature, the agent inventories the existing app, checks its navigation and user journeys, and decides where the feature belongs. The default audience is a nontechnical first-time user.

## What it prevents

- New tabs and menu items that duplicate an existing workflow
- Features hidden in the wrong page or settings section
- Visually impressive but confusing screens
- Inconsistent UI patterns, wording, and permissions
- Happy-path-only experiences without loading, errors, or revisit states

## Installation

**Hermes Agent**

Clone this repository and copy this directory to your Hermes skills folder:

    git clone https://github.com/josezuma/hermes-best-skills.git
    mkdir -p ~/.hermes/skills/feature-ux-architect
    cp hermes-best-skills/skills/feature-ux-architect/SKILL.md ~/.hermes/skills/feature-ux-architect/SKILL.md

Then ask Hermes to load the feature-ux-architect skill when adding a user-facing feature.

**Project-scoped coding agents**

Copy SKILL.md into your project's supported skills location, such as:

    .agents/skills/feature-ux-architect/SKILL.md

Optionally merge the relevant rules from AGENTS.template.md into the project's existing AGENTS.md. **Do not overwrite** an existing project AGENTS.md. Some agents require explicit instructions to read the skill.

## Example prompt

> Add a monitoring feature for AI agents. Before coding, inspect the existing routes, sidebar, settings, dashboard, roles, and related workflows. Apply feature-ux-architect to choose where users would naturally expect it, especially beginners. Give a short placement rationale, implement using existing components, and verify the full journey.

## Workflow

1. Inspect the real project and map existing relevant pages.
2. Identify users, jobs-to-be-done, and success criteria.
3. Select a home for the feature and compare alternatives.
4. Design the entire journey with beginner-friendly copy and states.
5. Document the brief Feature Placement Plan.
6. Implement within existing components and architecture.
7. Test navigability, clarity, edge cases, and build/lint where available.

**This is an instruction skill, not an autonomous scanner.** It needs a coding agent with repository access to inspect your project.

## License

MIT; see the repository license.
