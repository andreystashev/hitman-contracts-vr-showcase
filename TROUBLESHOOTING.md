# Troubleshooting

## The headset is not detected

Connect the headset in the PC VR application that matches your settings profile, then click **Check headset**. For Meta, enter Quest Link/Air Link. For Virtual Desktop, connect to Streamer and use VDXR. For SteamVR, wait until SteamVR reports the headset and controllers ready. See [connection profiles](INSTALLATION.md#headset-connection-profiles).

If detection cannot find a nonstandard installation, browse to its existing 64-bit OpenXR runtime JSON manifest. The launcher checks the selected profile and manifest without changing the system-wide runtime. An explicit profile does not fall back to Meta; fix the reported connection or choose another profile deliberately.

Close another running Hitman game/VR host before starting Contracts. Do not launch multiple copies of the game.

## Creating and sharing a support report

The collector creates a filtered technical ZIP to help investigate startup failures, crashes, flickering and connection problems. It creates the report locally; it does not fix the game or send anything automatically.

1. Reproduce the problem, then open **Contracts VR Settings**.
2. Select **Support → Create support report**.
3. Choose an output folder and wait for the completion message.
4. Find the generated `ContractsVR-Diagnostics-*.zip` in that folder. You can open it to review the JSON/text files.
5. Attach the ZIP to your bug report or send it to the developer manually. Include what you did, when the problem occurred, your headset model, selected connection profile and renderer. If comparing renderers, create a report after each attempt and label them.

If Settings cannot open, run `Collect-Contracts-Diagnostics.cmd` from the installed mod folder. Without an output override, it saves the report ZIP on your **Desktop**. Wait until the console says **Diagnostics saved**.

The collector works with an older installed version too, but the additional startup journal is available only after reproducing the problem with 0.1.0.13 or newer. No game launch, settings change or memory dump is performed by the collector.

The report includes selected build hashes/versions, render settings and counters, startup/error codes, Windows/GPU driver information and memory totals. Raw logs/settings and event messages, local paths, user/computer names, device IDs, network details, tracking poses, process lists, saves, recordings and memory dumps are excluded. Unknown free-form fields are omitted. Share the generated **report ZIP**, not the collector ZIP or a copy of the game folder.

## A crash before the main menu

Use **Support → Create support report** after the failure. This works while the launcher supervises a running game as well. Choose a local output folder, review the ZIP, then share it manually if you want help. No upload occurs. The separate `Collect-Contracts-Diagnostics.cmd` provides the same collector if the settings window cannot open.

The report contains selected technical fields: game/mod hashes and versions, graphics and connection settings, captured dimensions, startup stages, API error codes, Windows/GPU driver versions, memory totals and recognized Windows fault module/code/offset fields. Raw logs/configs/events, paths, account/computer names, device IDs, network details, tracking poses, process lists, game files, saves, recordings and memory dumps are excluded. Unrecognized free-form information is omitted; unknown module names are reported as `other-module`.

Each launch writes a small local startup journal, including capture-device creation and hook installation stages. An `exception-observed` entry is a first-chance observation and may have been handled by the game. It does not by itself prove that exception caused the final exit.

Exit code **3221225477 / 0xC0000005** means an access violation. It does not establish that RAM or VRAM ran out. The fault module, offset and last completed stage are needed to investigate. See [Microsoft's access violation explanation](https://learn.microsoft.com/en-us/shows/inside/access-violation-c0000005-read-or-write).

First check that the selected Steam game runs normally outside the mod. Keep the exact supported executable; do not apply a 4 GB/no-CD executable patch, which changes the verified build. If several old mod packages or renderers were used, compare their identities in the report rather than copying DLLs between installations. The compatibility renderer option provides a reversible comparison.

If there is an actual allocation error, close unneeded memory-heavy applications and compare a lower game render resolution. Check Windows Task Manager's **Memory → Committed** value against its limit. If the page file was disabled, a system-managed page file with sufficient free disk space is a reasonable baseline. This changes the system commit budget, not the game's 32-bit address-space limit. The mod does not change these Windows settings. See [Microsoft's page file guidance](https://learn.microsoft.com/en-us/troubleshoot/windows-client/performance/how-to-determine-the-appropriate-page-file-size-for-64-bit-versions-of-windows).

## Flickering during gameplay or cutscenes

The updated OpenXR host retains the last complete image in each active headset frame; a corrected timing path previously could submit an empty frame between game updates. That fix does not identify every possible flicker on every backend. Compare the same scene using **DXVK** and **Original / previous renderer**, restarting the game between changes. Report the connection profile, renderer, whether menus also flicker, and whether the scene flickers with the headset held still. Create one support report per renderer so the results can be compared.

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

Prefer the filtered support report from Settings. Raw logs and crash dumps can contain local paths and other personal information; they are deliberately excluded from that report. Never upload the game executable, game assets or a whole memory dump to a public issue.
