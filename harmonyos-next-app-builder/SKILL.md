---
name: harmonyos-next-app-builder
description: Build, review, or refactor HarmonyOS NEXT / OpenHarmony native applications with ArkTS, ArkUI, HAP/HAR/HSP modules, permissions, routing, storage, networking, WebView bridges, media UI, and DevEco build/test flows. Use when working on `.ets`, `.arkts`, `module.json5`, `oh-package.json5`, ArkUI components, HarmonyOS NEXT app architecture, or migration from Android/Web/Flutter patterns into native HarmonyOS.
---

# HarmonyOS NEXT App Builder

## Overview

Use this skill to turn a HarmonyOS NEXT feature request into a maintainable ArkTS/ArkUI implementation plan, then code or review it against common open-source project patterns.

For project evidence, strengths, weaknesses, and source links, read `references/research.md` when choosing architecture, dependencies, or tradeoffs.

## Workflow

1. Inspect the repo shape before editing: `entry/src/main/ets`, `module.json5`, `oh-package.json5`, `build-profile.json5`, `AppScope`, module boundaries, API level, and any HAR/HSP packages.
2. Classify the work:
   - UI feature: ArkUI component tree, state ownership, navigation, resource files, previewability.
   - Device/platform feature: permissions, abilities, background task, file/media access, system capability checks.
   - Hybrid feature: WebView bridge, JSBridge, local resource loading, message validation.
   - Data feature: request layer, persistence, cache invalidation, secure storage.
3. Prefer a small vertical implementation: route/page, state model, service wrapper, tests or preview harness, then integration.
4. Keep API-level assumptions explicit. If the code targets API 11/12/Next, do not silently use APIs from another level.
5. Verify with the repo's existing command path first: DevEco/HVigor scripts, `ohpm`, unit tests, linter, or project-specific documentation.

## ArkTS And ArkUI Rules

- Use typed state models and service interfaces; avoid passing raw JSON through component trees.
- Put side effects in lifecycle-safe services or view models rather than directly inside deeply nested UI builders.
- Keep ArkUI pages dense and predictable: page-level layout, reusable components, resource constants, then platform calls.
- Treat async calls as failure-prone: loading, empty, permission-denied, offline, and retry states should be visible in the UI.
- For WebView/JSBridge work, validate message origin, schema, command name, payload size, and callback lifecycle before exposing native APIs.

## Architecture Checklist

- Module choice: keep app shell in HAP; move shared UI, utilities, or SDK wrappers into HAR/HSP only when reuse or isolation is real.
- Permissions: declare only required permissions, request runtime authorization near the feature, and handle denial.
- Navigation: centralize route names and parameters; avoid ad hoc string routes in button handlers.
- Resources: use app resources for strings/colors/images; avoid hardcoded user-visible text in component code unless the project already does.
- Dependency risk: check license, maintenance, API level, native binary footprint, and whether the package is HarmonyOS NEXT native or a wrapper.
- Performance: watch long lists, image/video surfaces, WebView, animation, storage hot paths, and unnecessary recomposition.

## Use The Research

Read `references/research.md` when:

- Selecting examples to imitate.
- Comparing app, utility, WebView, and rendering-engine project patterns.
- Explaining why a dependency or architecture is risky.
- Writing a review summary with project evidence.
