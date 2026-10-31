# Hitman: Contracts VR - Release history and current status


This is the maintained English record of released changes, validation and known
limitations. Update this document for each release instead of creating separate
version-named validation reports. Older sections describe their release at the
time; the current-status section takes precedence.

## Current published release

**0.1.0.15 Review**, published **31 October 2026**:
[download and release assets](https://github.com/andreystashev/hitman-contracts-vr-showcase/releases/tag/v0.1.0.15-review).
It is a published prerelease, not a final stable release.

Installer: `ContractsVR-0.1.0.15-Setup.exe` (6,527,917 bytes).
SHA256: `60faa823a3b1ff88329e8ee0579da513da34004a664141098cccb8fd88856fbf`.
The published installer is the user-approved build; documentation maintenance
does not replace that binary or change its release tag.

| Area | Current status |
| --- | --- |
| D3D9On12 | Default for fresh bundled installations; GPU scene-image sharing with compatibility checks and CPU fallback. Existing explicit renderer choices are preserved when loading settings. |
| Original / DXVK | Available; CPU scene capture with direct host uploads and complete stereo-pair retention. |
| Foreground fog / Enfield optic | Accepted fixes included. |
| Night vision | Native postfilter retained at the user's request; silhouettes and geometry artifacts remain unresolved. Rejected shader experiments are excluded. |
| Stereo | Alternating eyes across game updates; simultaneous two-eye rendering is not implemented. |
| OpenGL | Incomplete effects backend; hidden in release settings. |
| Original direct-backbuffer experiment | Disabled by default following reported flashing. |
| Shared launcher/core refactor | Separate development branches; not part of this performance release. |

The approved performance-release scope is included. The incomplete/rejected work
listed above must not be presented as shipped fixes. Support for every GPU,
driver, headset or game-code patch has not been established.

## Update in 0.1.0.15

Close the game and launcher before updating. The installer resets mod settings
while preserving recordings and game saves; select your connection profile again.

- Optional **D3D9On12** renderer with GPU-only scene-image sharing to the VR host, a real compatibility probe and safe renderer restoration. D3D9On12 is the default; Original and DXVK remain available.
- Preserved DISCARD updates for small dynamic vertex buffers in the bundled D3D8 conversion layer, removing a large synchronization bottleneck in smoke-heavy scenes.
- Direct host uploads for Original/DXVK and coherent complete-eye-pair retention for CPU and GPU transports, reducing transfer overhead and mismatched eye updates.
- Corrected native fog coverage for the VR body and held-item submeshes, fixing sky transparency while preserving the game's postfilter.
- Corrected depth handling for the owned sniper overlay, fixing the Enfield Enforcer reticle disappearing behind scene geometry.
- The original night-vision appearance is retained. Its reported native postfilter artifacts are not fixed in this update.

D3D9On12 is optional and depends on Windows, driver and same-GPU image-sharing
support. Rendering still alternates eyes; game render rate is not headset display
rate. Compatibility and performance vary by system and scene.

## Update in 0.1.0.14

Close the game and launcher, then run the new installer. Installation resets mod settings to defaults, including controller and connection preferences; recordings and game saves are retained. Select your headset connection again in Settings.

- OpenXR controller hands use grip position with aim orientation; controller input is cleared when the OpenXR session loses focus. Two-handed grips and aiming still need testing across headset and controller combinations.
- Switching connection profiles clears the previous runtime override, preventing an old Virtual Desktop path from silently taking precedence over SteamVR. The installer also replaces old mod settings with clean defaults. The SteamVR runtime and headset were detected in a local launcher check; gameplay and other headset combinations still need verification. Virtual Desktop / VDXR has reported connection problems and remains unverified.
- Original / previous renderer is the recommended default. DXVK is available as an alternative and may be slightly faster, but can cause crashes, flickering or visual artifacts. Native OpenGL is not offered in the settings.
- The installer restores missing mod files and resets mod configuration, while preserving recordings, game files and saves.

Automated build, controller, launcher and installer checks passed. A successful headset detection is not a full gameplay test.

## Update in 0.1.0.13

This is a fix update to the Review Version. Close the game and old launcher, then run the new installer. Use **Settings > Support > Create support report** for a local diagnostic ZIP; [usage instructions](https://github.com/andreystashev/hitman-contracts-vr-showcase/blob/main/TROUBLESHOOTING.md#creating-and-sharing-a-support-report) explain the process. Nothing is uploaded automatically.

- Local support report button with allowlisted technical fields and no automatic upload. Raw logs, paths, personal/device identifiers and memory dumps are excluded.
- Startup phase and bounded exception observations to diagnose failures before the VR host starts.
- Corrected OpenXR frame submission between game-image updates and retained menu images during capture stalls.
- Original / previous renderer is the recommended default. DXVK may be slightly faster but can cause errors or artifacts.
- Visible game INI resolution and VirtualStore conflict warning; no automatic 4K selection or legacy width/height override.
- Native cheat and startup mission selector options, with game-path-specific preferences and preserved saves.
- Installer repair after manual folder deletion and safe relocation of a registered previous copy, with preserved user files and verified cleanup after successful installation.

Automated tests cover the corrected paths. Different headsets, drivers and renderers still need real gameplay testing; the pre-menu crash reported on an RTX 5080 is not yet reproduced or confirmed fixed.

A community VR conversion for the original **Hitman: Contracts (2004)**. This Review Version lets you see and experience the game's levels in VR while further VR interactions are developed.

## In this release

- Native stereo camera, head tracking, controller-driven arms and weapons on supported Steam 1.75 and legacy PC 1.74 executables.
- **Quest Link / Air Link (Meta)** output plus an **OpenXR** host for **Virtual Desktop / VDXR**, **SteamVR**, and compatible active OpenXR runtimes.
- Automatic and explicit connection profiles following the Blood Money VR settings layout, with validated runtime JSON selection where needed.
- Runtime choice applies only to the launched mod. Windows' global OpenXR runtime, default audio device and microphone are not changed.
- Automatic headset audio, Original, DXVK and optional D3D9On12 rendering choices, preserved game resolution and VSync disabled on the DXVK game presentation path.
- English settings, control hints and mod menus; transparent action menu and health/ammunition information beside the left hand.
- The Steam Crosshair rendering fix. **Crosshair is off** and **Controller help is on** by default.
- A per-user installer with separate launch/settings shortcuts; updates reset mod settings to defaults.

## Review Version limitations

Not all VR features are implemented or polished. Weapon swapping/dropping and immersive item/body handling remain experimental. Room-scale walking is not implemented. Use the native inventory and action menus when an interaction is awkward or unavailable.

The user reported Meta and Virtual Desktop tests with the rendering fixes. Recorded sessions cover Meta D3D9On12/DXVK and Virtual Desktop D3D9On12/DXVK/Original; one intended Meta Original run actually selected D3D9On12, so Meta Original coverage is missing. SteamVR headset gameplay and every headset/controller combination remain unverified. Please include your selected profile, runtime and controller model when reporting results.

See the [installation guide](INSTALLATION.md), [controls](CONTROLS.md) and [troubleshooting guide](TROUBLESHOOTING.md). The public project is [Hitman: Contracts VR Showcase](https://github.com/andreystashev/hitman-contracts-vr-showcase).

## Performance evidence for 0.1.0.15

Measurements below use RTX 4060 and the supported Steam executable. They measure
**game presents**, source eye images or transfer wall time, not headset displayed
FPS. D3D renders alternating eyes. Different scenes/resolutions are separate tests.

| Controlled change | Before | After | Result |
| --- | ---: | ---: | --- |
| D3D9On12 small dynamic-buffer DISCARD fix, Hunter and Hunted smoky room, 1600x1200, same-process ABBA | 84.7-85.0 presents/s | 209.6-211.7 presents/s | About 2.48x / +148% |
| Buffer-lock wall time in that ABBA test | 7.24-7.33 ms/frame | 0.674-0.676 ms/frame | About 91% less lock wait |
| Original CPU-to-host direct upload, same smoky room, 1600x1200 | 1.12-1.13 ms/image | 0.617-0.635 ms/image | About 44% lower host transfer time; game rate remained about 60 presents/s |

The first comparison isolates the conversion-layer fix, not the complete
0.1.0.14-to-0.1.0.15 update. The transfer comparison isolates the old and new host
upload paths. Neither is a universal release-to-release FPS percentage.

At 3840x2160, an additional diagnostic recorded about 123.6 D3D9On12 presents/s,
58.4 DXVK and 37.8 Original. Relative to that Original reference, DXVK was about **+55% (1.55x)** and
D3D9On12 about **+227% (3.27x)**. Settings label these as an approximate
RTX 4060 / 4K example. Those runs were separate processes with nonidentical
smoke/orientation and are references, not controlled renderer comparisons.
The faster Original direct-backbuffer experiment is **off by default** after a
reported native-driver flash; its 53% diagnostic improvement is not a default
release claim.

User Meta/Virtual Desktop runs also showed substantially higher source cadence
on D3D9On12, with approximately zero scene readback time. Those sessions used
different scenes and durations. One intended Meta Original run actually selected
D3D9On12; it must not be reported as Meta Original coverage.

No controlled combat or identical complete 0.1.0.14/0.1.0.15 headset comparison
is available. These figures do not establish a universal upgrade percentage.
Raw measurement JSON remains in the private development repository's
`tools-read/results/`; public notes summarize the evidence without publishing
private captures or machine paths.

## Validation of the published build

- Full build: 91 automated suites; 102 launcher settings checks.
- Renderer switching: 59 reversible checks in private game copies.
- Real GPU foreground/optic tests: system D3D8, DXVK and D3D9On12,
  including reset/resize and depth-state restoration after failed draws.
- Packaging: 26 runtime hashes, 14 installer staging tests, 12 public staging
  tests and 214 isolated installer workflow checks.
- User confirmed the Enfield reticle fix and reported the foreground repair
  working across tested connections/renderers. This does not imply a fresh
  final-build headset run for every backend or system.
- Public download size and SHA256 verified after publication.

## Earlier development, consolidated

The October 2026 comfort/gameplay iterations preceded the numbered releases
above. They added native controller hands and aiming, separate firing/reload
paths, support grips, scope entry, native melee animations, camera/root-motion
smoothing, cinematic-screen handling, map/floor navigation, inventory scrolling,
cursor ownership, and the wrist action/health/ammunition UI. Tests cover the
production adapters and supported executable profiles; isolated fixtures and
synthetic tracking runs are not complete headset acceptance tests.

The early OpenGL replay/capture experiments remain development research. Missing
effects prevented promoting that backend. The old hand-marker roadmap and
version-named validation reports are historical, superseded by this document
and the current player guides. Their originals are recoverable from Git history
at source release tag `v0.1.0.15-review`; measurement fixtures remain versioned.

## Maintenance policy

- Keep one current-status section and append released changes here; do not add
  per-experiment README or validation documents.
- Keep build outputs and private game copies outside tracked source. Old local
  build outputs may be archived under ignored `.cache-build/archived-builds/`.
- Keep original release binaries, hashes and tags immutable. Documentation-only
  maintenance does not require a new runtime version.
- Merge accepted work into `main`; remove superseded maintenance branches only
  after checking their changes. Preserve independent experimental work until it
  has been reviewed.
