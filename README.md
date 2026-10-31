# Hitman: Contracts VR — Review Version

**[Download Review Version 0.1.0.15 — Performance update](https://github.com/andreystashev/hitman-contracts-vr-showcase/releases/tag/v0.1.0.15-review)** | [All releases](https://github.com/andreystashev/hitman-contracts-vr-showcase/releases)

[Release history, current status and measured performance](RELEASE-NOTES.md) is the maintained record of changes and known limitations.

A community VR mod for the original **Hitman: Contracts (2004)** on PC, with native engine stereo rendering, head tracking and tracked controllers.

This **Review Version** is intended to let you see and experience the game's levels in VR. It is a work in progress, with incomplete and experimental VR interactions. It is not a finished full-immersion conversion: convenient weapon swapping/dropping and immersive object/body handling still need work.

You need your own copy of the game. This project does not include game files and is not affiliated with IO Interactive or the game's publishers.

## What it does

- Renders the game world in stereo using the game's camera and visibility system.
- Tracks your head and drives the original character's arms and held weapons from the controllers. OpenXR controller poses use grip position with aim orientation, and stale input is cleared when the session loses focus.
- Supports separate firing hands, native weapon reloads and two-handed support grips. Item/body interactions are experimental.
- Preserves melee attack animations and shows scripted cameras and cutscenes on a virtual screen.
- Places a transparent action menu and compact health/ammunition information beside the left hand while you hold **X**.
- Provides controller navigation for the game's menus, inventory, map and briefing.
- Routes game audio to the active headset without changing the Windows default audio device.

## Requirements

- Windows 10/11, 64-bit.
- A supported original PC executable: Steam **1.75**, or the supported legacy **1.74** build. See [installation](INSTALLATION.md) for the exact executable hashes.
- A connected PC VR headset and its runtime: **Meta Quest Link / Air Link**, **Virtual Desktop / VDXR**, **SteamVR through OpenXR**, or another compatible active OpenXR runtime.
- Tracked controllers and a GPU/driver with the VR runtime's D3D11 graphics support. DXVK additionally needs a compatible Vulkan driver; D3D9On12 has additional Windows/D3D12 sharing requirements. Meta PC software is required only for the Meta profile.

Choose the matching connection profile in settings. Explicit VDXR and SteamVR profiles select their detected runtime for this mod process; changing profiles clears the previous custom runtime path; they do not change Windows' global OpenXR runtime. The generic OpenXR profile uses the active runtime unless you choose a runtime JSON manifest. See [connection setup](INSTALLATION.md#headset-connection-profiles).

## Install and play

1. Download `ContractsVR-<version>-Setup.exe` from the [Releases page](https://github.com/andreystashev/hitman-contracts-vr-showcase/releases).
2. Run the installer, select your `HitmanContracts.exe`, and install the mod in its own folder.
3. Connect the headset through your chosen PC VR application.
4. Open **Contracts VR Settings**, verify the game path and select **Automatic** or the matching connection profile.
5. Click **Save & play**, then load a mission using the controllers.

The mod follows the game's resolution; the launcher preserves it. **D3D9On12 (DirectX 12)** is selected by default and checks GPU-sharing support before changing game DLLs. Choose **Original (DirectX 8)** for compatibility, or **DXVK (Vulkan)** as an alternative. Renderer settings show approximate gains from an RTX 4060 / 4K example; results vary by scene and system. Game presentation VSync is disabled for DXVK and D3D9On12; headset refresh and reprojection remain controlled by the VR runtime.

The Modifiers page also offers native **cheats** and **Start with the mission selector**. These options apply on the next mod launch and preserve saves. Disabling the mission selector restores the previous startup scene when it was saved by this setting.

After a problem, use **Settings → Support → Create support report**. The report stays on your PC until you choose to share it. It contains selected technical fields, with no raw logs/configuration, local paths, user/device identifiers or memory dumps. See [how to create and share a support report](TROUBLESHOOTING.md#creating-and-sharing-a-support-report).

## Settings

Connection profiles: **Automatic**, **Quest Link / Air Link (Meta)**, **Virtual Desktop / VDXR**, **SteamVR (OpenXR)** and **OpenXR**. Automatic checks an available Meta headset first, then OpenXR. Explicit profiles report their own connection problems without silently switching to a different backend.

The settings window follows the same connection/game and modifiers page layout as Blood Money VR.

| Modifier | Release default | Effect |
| --- | --- | --- |
| Crosshair | **Off** | Show weapon aiming markers. Sniper optics are handled separately. |
| Controller help | **On** | Show compact English button labels beside the tracked hands during gameplay. |

The action menu and its health/ammo information work independently of Controller help. Restart VR after changing Controller help. Crosshair changes are read while the game is running.

## Controls and help

See [the controls guide](CONTROLS.md) for the complete controller layout, [installation](INSTALLATION.md) for setup and removal, and [troubleshooting](TROUBLESHOOTING.md) for common problems and recording requirements.

Locomotion uses the sticks; room-scale walking is not implemented. Performance depends on the game scene, rendering resolution and headset settings. Save frequently and report the release version, game executable version, connection method and steps needed to reproduce an issue.

## About this repository

This is the public documentation, support and release repository. Development history, personal settings, game assets, recordings and crash dumps are not published here. The repository's visibility does not grant a source-code license for the mod. Bundled dependencies retain their own licenses; see [third-party notices](THIRD-PARTY-NOTICES.md).
