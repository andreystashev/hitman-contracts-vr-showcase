# Hitman: Contracts VR 0.1.0.13 - Review Version

## Update in 0.1.0.13

This is a fix update to the Review Version. Close the game and old launcher, then run the new installer. Existing settings are preserved. Use **Settings > Support > Create support report** for a local diagnostic ZIP; [usage instructions](https://github.com/andreystashev/hitman-contracts-vr-showcase/blob/main/TROUBLESHOOTING.md#creating-and-sharing-a-support-report) explain the process. Nothing is uploaded automatically.

- Local support report button with allowlisted technical fields and no automatic upload. Raw logs, paths, personal/device identifiers and memory dumps are excluded.
- Startup phase and bounded exception observations to diagnose failures before the VR host starts.
- Corrected OpenXR frame submission between game-image updates and retained menu images during capture stalls.
- DXVK remains the default; the previous renderer can be restored for compatibility comparisons without mixing renderer files.
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
- Automatic headset audio, DXVK rendering, preserved game resolution and VSync disabled on the game presentation path.
- English settings, control hints and mod menus; transparent action menu and health/ammunition information beside the left hand.
- The Steam Crosshair rendering fix. **Crosshair is off** and **Controller help is on** by default.
- A per-user installer with separate launch/settings shortcuts and preservation of settings during updates.

## Review Version limitations

Not all VR features are implemented or polished. Weapon swapping/dropping and immersive item/body handling remain experimental. Room-scale walking is not implemented. Use the native inventory and action menus when an interaction is awkward or unavailable.

The installed Meta path and Steam Crosshair fix have been checked in the headset. The new OpenXR backend and connection-selection paths have automated coverage; VDXR and SteamVR headset sessions have not yet been verified for this release. Please include your selected profile, runtime and controller model when reporting results. Support for every headset/controller combination or game-code patch is not implied.

See the [installation guide](INSTALLATION.md), [controls](CONTROLS.md) and [troubleshooting guide](TROUBLESHOOTING.md). The public project is [Hitman: Contracts VR Showcase](https://github.com/andreystashev/hitman-contracts-vr-showcase).
