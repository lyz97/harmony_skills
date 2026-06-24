# Research Notes: HarmonyOS AI Coding Skills

Collected on 2026-06-24 from GitHub API/search results. Re-check before recommending "latest" or installing anything.

## Direct Skill / Knowledge-Pack Candidates

| Project | Stars | Last push | Scope | Strengths | Weaknesses / caution |
| --- | ---: | --- | --- | --- | --- |
| [linhay/harmony-next.skills](https://github.com/linhay/harmony-next.skills) | 231 | 2026-06-18 | Expert guidance for HarmonyOS NEXT API 12+, DevEco operations, performance tuning, HAP/HAR/HSP architecture, automation testing | Most directly shaped like a skill repository; focused on NEXT development; active in June 2026 | No license metadata from GitHub API; inspect repository before copying content |
| [DengShiyingA/harmonyos-ai-skill](https://github.com/DengShiyingA/harmonyos-ai-skill) | 149 | 2026-06-17 | HarmonyOS NEXT knowledge pack generated for Claude Code, Cursor, Copilot, Codex, Gemini CLI, Windsurf, ChatGPT, and other tools | Multi-assistant output, explicitly targets ArkTS/ArkUI and AI coding workflows; MIT license | Generated multi-tool output can be verbose; merge only the parts that match the local assistant and repo |

## Related Reference Projects

| Project | Stars | Scope | How to use it |
| --- | ---: | --- | --- |
| [Awesome-HarmonyOS/HarmonyOS](https://github.com/Awesome-HarmonyOS/HarmonyOS) | 19903 | Curated HarmonyOS list | Use as discovery index, not as implementation authority |
| [fenwii/OpenHarmony](https://github.com/fenwii/OpenHarmony) | 1355 | OpenHarmony/HarmonyOS technical materials | Use for broad learning and terminology; verify code/API details elsewhere |
| [waylau/harmonyos-tutorial](https://github.com/waylau/harmonyos-tutorial) | 1736 | HarmonyOS tutorial materials | Use for onboarding, not necessarily latest NEXT production patterns |
| [ohosvscode/arkTS](https://github.com/ohosvscode/arkTS) | 852 | ArkTS VSCode tooling | Use to understand editor/linter expectations |

## Distilled Integration Pattern

1. Use public AI skills as seed material, not as unquestioned truth.
2. Convert broad prompt packs into concise Codex skill instructions plus optional `references/`.
3. Keep skill frontmatter trigger-rich: include ArkTS, ArkUI, DevEco, HAP/HAR/HSP, module files, and API-level tasks.
4. Tie every rule to either the local repo, official docs, or a clearly named reference project.
5. Revalidate after every major SDK/API change.

## Evaluation Checklist

- Does the skill identify when to trigger, or only describe HarmonyOS generally?
- Does it separate stable workflow from volatile API tables?
- Does it mention DevEco/HVigor/ohpm/module files?
- Does it have a license that permits adaptation?
- Does it include validation commands or just writing advice?
- Does it avoid hardcoding one assistant's behavior into another assistant's config?

## Sources

- GitHub API metadata for the projects above, queried 2026-06-24.
- Search phrases included `HarmonyOS NEXT Codex skill GitHub`, `鸿蒙 开发 skill Codex HarmonyOS NEXT AI skill GitHub`, and topic searches for `arkts` and `harmonyos`.
