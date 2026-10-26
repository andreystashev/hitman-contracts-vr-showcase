# Installation and removal

## Supported game builds

Use your own installed PC copy of **Hitman: Contracts (2004)**. The installer and launcher check `HitmanContracts.exe` before enabling native hooks.

| Build | SHA-256 of the supported executable |
| --- | --- |
| Steam 1.75 | `189f8ce2e40603db1387266e960fcf102c479ad4de83d31b1cbfe3647b6cd702` |
| Legacy PC 1.74 | `51a17df39de3d725484c6b4b4a96bf0d45b4ab6e82effc80230e58ca7859f09d` |

A matching version label alone is not sufficient. Replaced executables and patches that change executable code may not be supported. Unknown builds are rejected rather than assigned another build's memory addresses. No game executable or game assets are supplied.

## First installation

1. Install and run the original game normally once. Choose the desired graphics resolution in the game or your compatible resolution mod.
2. Close the game and its VR host before installing or updating the mod. Save any progress first.
3. Run `ContractsVR-<version>-Setup.exe` and select the supported `HitmanContracts.exe`. Steam libraries are searched automatically; use Browse if needed.
4. Choose a separate mod folder. The default is under your Windows user account. Keep the mod outside the game folder.
5. Finish installation. The installer creates shortcuts for **Contracts VR** and **Contracts VR Settings**.
6. Connect the headset through the PC VR application you intend to use. Follow the connection setup below.
7. Open **Contracts VR Settings**, check the game path, choose **Automatic** or your specific connection profile, and click **Check headset**. Click **Save & play** when the check passes.

The launcher installs the bundled DXVK wrapper reversibly into the selected game folder when starting the game. It keeps a backup of the previous wrapper state. It does not replace `HitmanContracts.exe`.

## Headset connection profiles

| Profile | Setup |
| --- | --- |
| Automatic | Start your PC VR application and connect the headset. The launcher checks Meta first, then the available OpenXR runtime. Use an explicit profile when more than one application is installed and you want a particular one. |
| Quest Link / Air Link (Meta) | Install Meta Quest Link on the PC, connect by cable or Air Link, and enter the PC VR environment in the headset. This path uses the installed Meta runtime. |
| Virtual Desktop / VDXR | Start Virtual Desktop Streamer, connect from the headset, and use VDXR for the PC VR session. Select the Virtual Desktop profile; the launcher finds the installed 64-bit VDXR manifest. Meta Quest Link is not required for this path. |
| SteamVR (OpenXR) | Start SteamVR and wait until the headset/controllers are ready, then select the SteamVR profile. The launcher finds the installed 64-bit SteamVR OpenXR manifest. |
| OpenXR | Connect the headset through its PC software. This profile uses the active OpenXR runtime or a runtime JSON manifest selected in settings. The runtime must support D3D11 and tracked controllers. |

**OpenXR runtime JSON** is optional when a matching runtime can be detected. Use Browse only if the software is installed in an unusual location or you deliberately want a specific compatible runtime. Select its existing runtime `.json` manifest, not a DLL or the SteamVR executable. A supplied manifest is validated before launch.

The selection applies only to the mod and its child host through `XR_RUNTIME_JSON`. The launcher does not rewrite Windows' global OpenXR selection or start another backend when an explicit connection profile fails. Close the game before changing profiles; a working session is not moved to another runtime mid-game.

This release adds the OpenXR paths with automated coverage. VDXR and SteamVR headset sessions have not yet been verified for this release; report the selected profile, runtime and controller model when testing them.

## Resolution, rendering and sound

The game resolution is preserved automatically, including a supported high-resolution setup. Higher render resolutions cost performance; there is no requirement to choose a resolution in the VR launcher.

The settings window displays the selected game's INI resolution. If Steam and the mod seem different, check that both start the same game installation and use the same Windows account without administrator mode. The launcher warns when a separate Windows VirtualStore copy of the INI exists; it does not merge or delete either copy. The support report includes captured frame dimensions, which may differ from the requested INI value if the game or a resolution mod changes them.

**DXVK (recommended)** remains the default. **Original / previous renderer (compatibility test)** restores the exact files saved before the mod installed DXVK, which may include Steam's WineD3D or an existing custom renderer. On a clean game without a backup it leaves the existing renderer alone. Unknown replacements or a missing backup are reported rather than overwritten. Close the game before switching. Performance and visual results vary; this is a comparison option, not a promise that every renderer is tested on every GPU. VSync is disabled through DXVK configuration; the previous WineD3D path uses its supported swap control when available, while Windows composition can still affect presentation.

On **Modifiers**, **Enable cheats and console** enables the game's native cheat commands. **Start with the mission selector** opens the original level selection scene instead of the startup sequence. Changes apply on the next mod launch; selecting a different game path reloads that installation's options. Existing custom startup scenes are preserved unless you explicitly change the mission selector option. No save files or executable bytes are modified.

DXVK is the default rendering path. The launcher disables its VSync presentation wait. This does not disable the headset runtime's refresh timing or reprojection.

The game is routed to the selected headset/runtime's audio endpoint. The launcher does not switch the Windows default speaker or microphone. If headset audio is unavailable or ambiguous, it reports that problem instead of silently choosing desktop speakers. Reconnect the selected PC VR application and check its headset audio output before retrying.

## Updating, moving or repairing an installation

Run the installer again to update or repair the existing mod folder. Missing mod files are restored, while settings and recordings are preserved. A manually deleted old folder no longer prevents choosing a new installation location; the uninstall registration is updated only when installation succeeds.

To move an installed copy, choose another separate mod folder. The installer copies recognized settings if the destination has no settings of its own. After the new installation succeeds, it removes verified, unmodified mod files and the verified old uninstaller from the registered previous location. Edited files, unknown files, settings and recordings remain in the old folder. The installer does not scan arbitrary folders for old copies or remove game/renderer files from the game installation.

Close the old launcher, game and VR host before updating or moving the mod. They are never terminated automatically. Choose separate folders outside the game and Windows directories, without nesting the new mod folder inside the old one or using a junction/symbolic link. After moving, use the updated shortcuts.


The release defaults are **Crosshair off** and **Controller help on**. Review the Modifiers page after an update.

## Removing the mod

Close the game and VR host, then use **Windows Settings → Apps → Contracts VR → Uninstall**. The installer removes the installed mod and its shortcuts; it does not remove the original game or its saves.

The game-folder DXVK wrapper is managed separately from the installed mod files. To return the game to its previous renderer, run the included renderer-restore script while the installed mod is still available, then uninstall. The restore operation verifies the backup before replacing files; retain the backup if it reports a conflict.
