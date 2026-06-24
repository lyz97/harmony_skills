# Research Notes: HarmonyOS NEXT Native Apps

Collected on 2026-06-24 from GitHub API/search results. Star counts change; re-check GitHub before making current popularity claims.

## Project Signals

| Project | Stars | Main signal | Strengths to borrow | Weaknesses / caution |
| --- | ---: | --- | --- | --- |
| [xiaobaigroup/ClashBox](https://github.com/xiaobaigroup/ClashBox) | 3878 | HarmonyOS NEXT proxy/VPN client tagged ArkTS/ArkUI | Real NEXT app domain, complex networking/VPN surface, active maintenance | GPL-3.0 license; domain-specific complexity; not every pattern fits ordinary apps |
| [ohosvscode/arkTS](https://github.com/ohosvscode/arkTS) | 852 | VSCode plugin for ArkTS navigation/completion/linting | Tooling insight, code intelligence, current activity | Editor extension patterns do not map directly to app runtime |
| [WinWang/HarmoneyOpenEye](https://github.com/WinWang/HarmoneyOpenEye) | 621 | ArkTS/ArkUI video/content app, API 9+, adapted to API 11+ | Clear learning app for UI, lists, detail pages, media/content flows | Last push 2024-08-14; API assumptions may be stale |
| [harmony-on-android/HOA](https://github.com/harmony-on-android/HOA) | 521 | Runs OpenHarmony HAP on Android | Useful for runtime boundary thinking and compatibility experiments | No license metadata; not a normal app architecture reference |
| [Wscats/openharmony-sheet](https://github.com/Wscats/openharmony-sheet) | 242 | OpenHarmony sheet/game/rendering engine | Canvas/rendering-heavy patterns and performance concerns | JavaScript-heavy; may not reflect idiomatic modern ArkTS |
| [751496032/DSBridge-HarmonyOS](https://github.com/751496032/DSBridge-HarmonyOS) | 178 | ArkTS and JavaScript bridge library | WebView bridge design, message boundaries, hybrid migration | No license metadata; bridge security must be reviewed before reuse |
| [787107497/harmony-utils](https://github.com/787107497/harmony-utils) | 117 | OpenHarmony/HarmonyOS utility package | Utility packaging, common helpers, developer ergonomics | Utility libraries can hide platform errors; audit APIs before adding |
| [OHPG/FinVideo](https://github.com/OHPG/FinVideo) | 53 | Jellyfin video client for HarmonyOS NEXT/OHOS | Media client workflow, player state, active 2026 maintenance | Smaller community; GPL-3.0 license |

## Distilled Patterns

1. Treat HarmonyOS NEXT as a native platform, not an Android skin. Projects with the strongest signal use ArkTS/ArkUI and platform-specific abilities directly.
2. Separate UI state, platform services, and transport/storage. This is visible across app-scale projects and reduces churn when APIs or permissions change.
3. Keep bridges narrow. DSBridge-style hybrid work is useful for migration, but every native command needs schema validation and a clear permission model.
4. Check license before borrowing code. GPL projects are useful for learning but may be unsuitable for direct incorporation into proprietary apps.
5. Active maintenance matters. HarmonyOS NEXT API levels move quickly; stale examples should be treated as conceptual references until verified in DevEco.

## Review Questions

- What API level and SDK does the project target?
- Is this an app, SDK, tool, or compatibility experiment?
- Are permissions declared and requested where the user action occurs?
- Are async failures represented in UI state?
- Are network, storage, and native bridge payloads typed and validated?
- Does a dependency's license permit the user's intended use?

## Sources

- GitHub API metadata for the projects above, queried 2026-06-24.
- Search topics used: `topic:harmonyos`, `topic:openharmony`, `topic:ohos`, `topic:arkts`, plus name/description searches for `HarmonyOS`, `OpenHarmony`, `OHOS`, and `ArkTS`.
