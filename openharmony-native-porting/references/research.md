# Research Notes: OpenHarmony/OHOS Native And Cross-Platform Porting

Collected on 2026-06-24 from GitHub API/search results. Re-check current repository state before making time-sensitive claims.

## Project Signals

| Project | Stars | Main signal | Strengths to borrow | Weaknesses / caution |
| --- | ---: | --- | --- | --- |
| [Tencent/MMKV](https://github.com/Tencent/MMKV) | 18626 | C++ key-value storage framework with OHOS support | Mature mobile native library, storage performance, multi-language ecosystem | License metadata is `NOASSERTION`; direct code reuse needs legal review |
| [nihui/opencv-mobile](https://github.com/nihui/opencv-mobile) | 3307 | Minimal OpenCV for many platforms including HarmonyOS | Portable C++ build discipline, small footprint, CV/media-heavy example | Native performance must be tested per device and ABI |
| [Tencent-TDS/KuiklyUI](https://github.com/Tencent-TDS/KuiklyUI) | 3219 | Kotlin Multiplatform UI framework with HarmonyOS among targets | Cross-platform UI architecture and dynamic delivery thinking | License metadata is `NOASSERTION`; framework adoption has high lock-in |
| [harmony-on-android/HOA](https://github.com/harmony-on-android/HOA) | 521 | Runs OpenHarmony HAP on Android | Compatibility-layer research and runtime boundary exploration | Not a production OpenHarmony app template; no license metadata |
| [wang-bin/avbuild](https://github.com/wang-bin/avbuild) | 661 | FFmpeg-style build tool for OHOS and many platforms | Cross-platform build automation and media dependency packaging | Shell/build-system knowledge may be hard to transplant directly |
| [wang-bin/fvp](https://github.com/wang-bin/fvp) | 345 | Flutter video player plugin across desktop/mobile | Plugin boundary and media playback portability | Flutter platform integration may not satisfy native UX/performance goals |
| [OpenHarmony-NET/OpenHarmony.Avalonia](https://github.com/OpenHarmony-NET/OpenHarmony.Avalonia) | 335 | .NET/Avalonia target for OpenHarmony | Non-TS runtime porting reference | Smaller ecosystem; verify device support and maintenance |

## Distilled Porting Principles

1. Separate "can compile" from "is production-ready." OHOS support in a project description is a start, not proof of lifecycle, permission, real-device, or package behavior.
2. Keep platform layers explicit. A stable ArkTS facade over native code is easier to test and replace than UI code calling raw native bindings.
3. Treat media, CV, storage, VPN/networking, and graphics as device-tested features. These areas are where emulator success most often hides defects.
4. Prefer minimal native surface area. Expose domain operations, not generic native escape hatches.
5. License metadata matters. High-star projects can still have unclear or restrictive license terms.

## Risk Checklist

- Build: Does the toolchain target OHOS correctly, without local absolute paths?
- ABI: Are all required architectures built and packaged?
- Runtime: What happens when a native library fails to load?
- Memory: Are buffers copied across ArkTS/native boundaries unnecessarily?
- Threading: Are callbacks marshalled back to the expected HarmonyOS execution context?
- Permissions: Are platform capabilities requested and denied gracefully?
- License: Is the license compatible with the user's distribution model?

## Sources

- GitHub API metadata for the projects above, queried 2026-06-24.
- Search topics used: `topic:ohos`, `topic:harmonyos`, `topic:openharmony`, plus name/description searches for `OHOS`, `HarmonyOS`, and `OpenHarmony`.
