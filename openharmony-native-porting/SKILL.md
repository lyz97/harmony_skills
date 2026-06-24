---
name: openharmony-native-porting
description: Port, wrap, or review native and cross-platform libraries for OpenHarmony/OHOS/HarmonyOS, including C/C++ NDK code, Node-API/NAPI bindings, Rust/Kotlin/Flutter integrations, media/CV/storage SDKs, ABI/build scripts, HAP/HAR packaging, and platform compatibility work. Use when files mention OHOS, OpenHarmony, HarmonyOS, NDK, CMake, native modules, `.so` libraries, FFI, or cross-platform mobile frameworks targeting HarmonyOS.
---

# OpenHarmony Native Porting

## Overview

Use this skill to evaluate whether existing native or cross-platform code can run on OpenHarmony/OHOS, then produce a porting plan with build, ABI, runtime, packaging, and license checks.

Read `references/research.md` when choosing examples, explaining tradeoffs, or citing high-star projects.

## Porting Workflow

1. Inventory the source: language, build system, native dependencies, dynamic libraries, generated bindings, platform APIs, and license.
2. Identify the target: OpenHarmony device, HarmonyOS NEXT app, OHOS library package, emulator, or compatibility experiment.
3. Map platform assumptions:
   - POSIX calls, file paths, permissions, sockets, threads, timers.
   - Graphics/media APIs, hardware acceleration, camera, codec, and surface ownership.
   - Storage, key-value data, encryption, sandbox path, and lifecycle.
4. Decide the integration layer: direct ArkTS wrapper, Node-API/NAPI, C ABI, Rust FFI, Flutter plugin, Kotlin Multiplatform, or HAR/HSP package.
5. Build the smallest proof: compile one target ABI, run a smoke test, then add feature coverage and packaging.
6. Document unsupported features explicitly instead of silently degrading behavior.

## Build And ABI Checklist

- Confirm OHOS SDK/NDK version, API level, architecture, STL/runtime, and CMake toolchain settings.
- Keep generated artifacts reproducible. Do not commit local absolute paths or machine-specific SDK paths.
- Audit transitive native dependencies for unsupported syscalls, assembly, SIMD, and platform-specific file/network behavior.
- Include load-time failure handling for missing `.so` files, ABI mismatch, or permission denial.
- Keep bindings typed and small. Expose stable domain APIs to ArkTS rather than leaking low-level pointers or raw buffers.

## Cross-Platform Judgment

- Borrow from multi-platform libraries for build organization, not blindly for app architecture.
- Prefer native OHOS/HarmonyOS APIs when the feature is platform-sensitive: permissions, lifecycle, media playback, VPN/network, secure storage, notifications.
- For UI frameworks such as Flutter or Kotlin Multiplatform, validate startup cost, package size, platform channel behavior, and whether platform-native UX is required.
- For media/CV/storage libraries, test real-device performance and memory pressure. Emulator-only success is weak evidence.
- For compatibility layers, treat them as research unless they match the production target and support model.

## Output Format

When asked for a porting plan, produce:

1. Compatibility verdict: likely, uncertain, or high-risk.
2. Required code changes: build, source, bindings, packaging, runtime guards.
3. Validation plan: compile, unit/smoke tests, device tests, performance checks.
4. Known risks: license, missing APIs, binary size, maintenance, real-device gaps.
5. Evidence: cite relevant examples from `references/research.md` or the current repo.
