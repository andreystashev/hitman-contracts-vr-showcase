# Third-party notices

Hitman: Contracts is a game by IO Interactive. Game names and trademarks belong to their respective owners. This community mod is independent and does not distribute the original game.

The mod does not grant a license to the game or to any third-party component beyond that component's own terms.

| Component | Use | License/notice |
| --- | --- | --- |
| MinHook, including Hacker Disassembler Engine | Native function hooks | [MinHook license](licenses/MinHook-LICENSE.txt) |
| Oculus PC SDK / LibOVR headers | Meta PC runtime interface | Copyright © 2014–2016 Oculus VR, LLC. All rights reserved. [SDK license](licenses/Oculus-SDK-LICENSE.txt) |
| OpenVR interface headers | Query the audio output selected by the user's installed SteamVR | [Valve/OpenVR BSD license](licenses/OpenVR-LICENSE.txt) |
| OpenXR SDK 1.1.65 | Bundled Khronos x64 loader and interface headers | [OpenXR Apache-2.0 license](licenses/OpenXR-LICENSE.txt) |
| JsonCpp | JSON parsing inside the OpenXR loader | [JsonCpp public-domain/MIT license](licenses/JsonCpp-LICENSE.txt) |
| DXVK 3.1.1 | Bundled x86 D3D8/D3D9 renderer wrappers | [DXVK license](licenses/DXVK-LICENSE.txt) |
| d3d8to9 | Optional modified x86 D3D8-to-D3D9On12 renderer | [BSD-2-Clause](https://github.com/crosire/d3d8to9/blob/main/LICENSE.md); license and pinned upstream revision accompany the DLL in `renderer-on12-x86` |
| LLVM / Clang | Compiler-provided code and toolchain notices | [LLVM license](licenses/LLVM-LICENSE.txt) |
| libc++ | Statically linked C++ standard library | [libc++ license](licenses/libcxx-LICENSE.txt) |
| libc++abi | Statically linked C++ ABI runtime | [libc++abi license](licenses/libcxxabi-LICENSE.txt) |
| libunwind | Statically linked exception-unwinding runtime | [libunwind license](licenses/libunwind-LICENSE.txt) |
| compiler-rt | Compiler runtime support | [compiler-rt license](licenses/compiler-rt-LICENSE.txt) |
| MinGW-w64 runtime | Windows C runtime startup/support code | [Runtime notices](licenses/MinGW-w64-runtime-LICENSE.txt) |
| winpthreads | Windows POSIX threading support | [winpthreads notices](licenses/winpthreads-LICENSE.txt) |

The Meta PC runtime itself is loaded from the user's installed Meta software and is not bundled with the mod. The Oculus SDK remains subject to its own terms, including its approved-platform provisions.

Microsoft D3D9On12, D3D12 and D3DX9 runtimes are supplied by the user's Windows/DirectX installation and are not redistributed here. The optional d3d8to9 modifications explicitly select On12 and preserve DISCARD on small dynamic buffers; upstream source and local changes are recorded in its `upstream.json`.

The SteamVR audio query loads OpenVR from the user's SteamVR installation for a background utility query; no OpenVR DLL is bundled. SteamVR remains responsible for its selected headset audio device.

The bundled OpenXR loader is built from the official Khronos OpenXR-SDK 1.1.65 source, commit `24a1f2b92d212501a2b1b8d30ffd53abf55fcfa8`. It is a loader, not a headset runtime, and does not include SteamVR, VDXR or Meta runtime binaries.

DXVK upstream: <https://github.com/doitsujin/dxvk/releases/tag/v3.1.1>. MinHook upstream: <https://github.com/TsudaKageyu/minhook>.

The Windows binaries are built with LLVM-MinGW and static runtime linkage. The runtime notices above are included with the binary distribution; the compiler toolchain itself is not included. LLVM component notices were taken from the compiler's recorded LLVM source revision, [`0d261d1ca552c95a8f007e061c787ac7132fbcbc`](https://github.com/llvm/llvm-project/tree/0d261d1ca552c95a8f007e061c787ac7132fbcbc). The original license texts retain their component-specific copyright and legacy-license sections.

The optional recorder uses the user's installed Python, FFmpeg and Python packages. These are separate installations; they are not included as part of this installer.

No overall open-source license for the mod is declared by this public documentation repository. Do not treat third-party licenses as licensing the mod's original code.
