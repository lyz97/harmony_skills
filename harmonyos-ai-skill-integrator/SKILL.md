---
name: harmonyos-ai-skill-integrator
description: Find, compare, adapt, and validate HarmonyOS NEXT / OpenHarmony AI coding skills, prompt packs, agent rules, and knowledge bases for ArkTS/ArkUI development. Use when a user asks to install or merge HarmonyOS AI skills, evaluate online HarmonyOS skill repositories, create Codex/Cursor/Claude/Gemini guidance from existing HarmonyOS docs, or keep an assistant aligned with DevEco, HAP/HAR/HSP, ArkTS, ArkUI, and API-level rules.
---

# HarmonyOS AI Skill Integrator

## Overview

Use this skill to evaluate external HarmonyOS AI coding skills and turn them into concise, current, locally usable guidance without copying stale or incompatible instructions blindly.

Read `references/research.md` before recommending a public skill or merging external guidance.

## Integration Workflow

1. Identify the target assistant surface: Codex skill, Cursor rules, Claude Code skill, Copilot instructions, Gemini CLI, Windsurf, or generic prompt.
2. Inspect the local repo first: HarmonyOS API level, DevEco/HVigor/ohpm setup, module structure, existing rules, and test commands.
3. Compare external skills by coverage, freshness, source discipline, and portability.
4. Extract durable rules:
   - ArkTS/ArkUI architecture.
   - DevEco/HVigor/ohpm commands.
   - HAP/HAR/HSP module boundaries.
   - Permissions and API-level caveats.
   - Testing, preview, lint, and performance workflows.
5. Remove assistant-specific noise that does not apply to the current tool.
6. Validate the resulting skill/rules with a realistic task: create a component, review a module, fix an ArkTS error, or plan an API migration.

## Selection Rules

- Prefer skills that cite official or repository-local sources over broad generated advice.
- Prefer small task-oriented rules over long encyclopedic dumps.
- Treat API-version claims as volatile; verify against the project and current docs before editing code.
- Do not merge conflicting style rules. Resolve conflicts by following the current repository first, then official docs, then external skills.
- Preserve license notices and attribution when adapting public repositories.

## What To Produce

When asked to integrate HarmonyOS AI skills, produce:

1. Candidate list with links, stars, last push date, and scope.
2. Strengths and weaknesses for each candidate.
3. A merged rule set or Codex skill plan with explicit exclusions.
4. Validation steps and the exact files changed.
5. Remaining gaps, especially API-level uncertainty and missing local build verification.

## Common Gaps To Fill

- Existing skills often know HarmonyOS concepts but not the user's repo commands.
- Some knowledge packs are broad and token-heavy; convert them into progressive disclosure with `references/`.
- Tool-specific syntax varies. A Cursor or Claude rule can inspire a Codex skill, but frontmatter, trigger descriptions, and validation differ.
- High-star app repos teach architecture, but they are not AI skills. Use them as evidence for rules, not as prompt packs.
