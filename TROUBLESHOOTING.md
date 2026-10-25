# Troubleshooting

## The headset is not detected

Connect the headset in the PC VR application that matches your settings profile, then click **Check headset**. For Meta, enter Quest Link/Air Link. For Virtual Desktop, connect to Streamer and use VDXR. For SteamVR, wait until SteamVR reports the headset and controllers ready. See [connection profiles](INSTALLATION.md#headset-connection-profiles).

If detection cannot find a nonstandard installation, browse to its existing 64-bit OpenXR runtime JSON manifest. The launcher checks the selected profile and manifest without changing the system-wide runtime. An explicit profile does not fall back to Meta; fix the reported connection or choose another profile deliberately.

Close another running Hitman game/VR host before starting Contracts. Do not launch multiple copies of the game.

## OpenXR starts but tracking or buttons are missing

Keep the headset awake and the PC VR application focused. A runtime losing focus clears gameplay input until focus returns. Use the runtime's controller bindings when its controllers do not have the Meta Touch button names used by the controls guide. This Review Version does not claim tested support for every headset/controller combination.

## The game executable is rejected

Select the supported original `HitmanContracts.exe`, not Steam itself or a shortcut. See [the supported hashes](INSTALLATION.md#supported-game-builds). Do not rename a different executable to bypass the check. Report your game's version and SHA-256 if you need support for another build.

## The view is offset or movement feels wrong

Look forward in a comfortable playing position and hold the right stick click to recenter. **F7** performs the same action while the game is focused. Locomotion uses the sticks; physical room-scale walking is not implemented.

## No sound in the headset

Confirm your selected PC VR connection is active and its headset audio output is available in Windows. For Virtual Desktop, check the Virtual Desktop audio output; for SteamVR, check the headset output used by SteamVR. Restart the game from the mod launcher after reconnecting. The launcher checks the route and reports a failure if it cannot select an unambiguous headset endpoint. The mod does not change Windows' default device or the microphone.

## Stutter or low frame rate

Reduce the game's render resolution or graphics settings and compare the same scene. A 4K desktop render can be substantially more expensive than a lower game resolution. VSync is already disabled on the bundled DXVK game presentation path. The headset refresh rate, compositor and any reprojection still have their own timing.

## Crosshair or controller help is missing

The release default is **Crosshair off**. Enable it on the Modifiers page and save. Markers are used for normal firearm aiming; they are hidden in menus, native optics and scripted/action views where an aiming marker would be inappropriate.

**Controller help** is on by default. It appears beside tracked hands during normal gameplay and hides during menus, actions and optics. Restart VR after changing this setting. Holding **X** shows the action menu and health/ammunition information independently of Controller help.

## Recording a video

Recording is an optional separate script, not a launcher page. Run `Record-Contracts-VR.cmd` from the installed mod folder before or after launching the game. The normal recording path includes the complete composited view: game, mod HUD, controller panels, native menus and cutscenes. It writes a continuous rectilinear **1920×1080 MP4**, with a 60 FPS output timeline by default. Source motion smoothness still depends on the game's actual frame rate.

The recorder requires **Python 3**, **FFmpeg**, and the Python `numpy` and `soundcard` packages for audio. These tools are not required to play the mod and are not installed automatically. FFmpeg must be available on PATH, or in the supported existing Virtual Desktop Streamer installation. Installing that application is not necessary when FFmpeg is already on PATH.

The default output folder is `recordings` beside the mod. Recording follows the game's headset audio route. It does not record the microphone by default. To finish the MP4, focus the recording console and press **Enter** or **Q**; **Ctrl+C** also stops it. Wait for the final save message before closing the console. Loading screens do not end the recording.

Advanced options are available through `Record-VR.ps1`, for example `-NoAudio`, `-Seconds 60` or `-Output <path>`. Avoid `-GameOnly` if you want mod HUD/panels in the video.

## Reporting a bug

Include the mod release version, supported game build, headset model, connection method, game resolution and reproducible steps. For a visual problem, state whether it affects gameplay, menus or cutscenes, and whether it appears while your head is still.

Logs and crash dumps can contain local paths and other personal information. Review them before sharing and send only what is needed for the report. Never upload the game executable, game assets or a whole memory dump to a public issue.
