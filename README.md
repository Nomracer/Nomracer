<h1 align="center">Gürkan (Nomracer) Şimşek</h1>

<p align="center">
  Unity developer. I care about what a game costs per frame on hardware people actually own.
</p>

<p align="center">
  <a href="https://nomracer.itch.io/"><img src="https://img.shields.io/badge/itch.io-play%20my%20games-FA5C5C?style=for-the-badge&logo=itchdotio&logoColor=white" alt="itch.io"></a>
  <a href="https://github.com/Nomracer/Crucible"><img src="https://img.shields.io/badge/Crucible-read%20the%20code-2E2E2E?style=for-the-badge&logo=github&logoColor=white" alt="Crucible"></a>
</p>

<img src="https://raw.githubusercontent.com/Nomracer/Nomracer/main/.assets/rule.svg" width="100%" height="3" alt="">

## Dead Frame

<p>
  <a href="https://nomracer.itch.io/dead-frame"><img src="https://img.shields.io/badge/▶%20play-itch.io-FA5C5C?style=for-the-badge&logo=itchdotio&logoColor=white" alt="Play Dead Frame"></a>
  <img src="https://img.shields.io/badge/horror-8B0000?style=for-the-badge" alt="Horror">
  <img src="https://img.shields.io/badge/windows-0078D6?style=for-the-badge&logo=windows&logoColor=white" alt="Windows">
  <img src="https://img.shields.io/badge/~30%20min-2E2E2E?style=for-the-badge" alt="30 minutes">
  <img src="https://img.shields.io/badge/VR%20port-in%20development-8B5CF6?style=for-the-badge" alt="VR port in development">
</p>

<a href="https://nomracer.itch.io/dead-frame">
  <img src="https://img.itch.zone/aW1nLzI4MTkyMjE1LnBuZw==/original/ooc3EM.png" width="420" align="right" alt="Dead Frame cover">
</a>

Psychological horror. You are a trainee in a Veyks encounter simulation. Survive four nights and get educated, because your life depends on it.

Subtitles and remappable controls. Two months of development, shipped and playable right now.

Currently porting it to VR.

<br clear="all">

<img src="https://raw.githubusercontent.com/Nomracer/Nomracer/main/.assets/rule.svg" width="100%" height="3" alt="">

## Crucible

<p>
  <a href="https://github.com/Nomracer/Crucible"><img src="https://img.shields.io/badge/source-github-2E2E2E?style=for-the-badge&logo=github&logoColor=white" alt="Source"></a>
  <img src="https://img.shields.io/badge/Unity%206-000000?style=for-the-badge&logo=unity&logoColor=white" alt="Unity 6">
  <img src="https://img.shields.io/badge/Burst-FF6B35?style=for-the-badge" alt="Burst">
  <img src="https://img.shields.io/badge/Job%20System-3B82F6?style=for-the-badge" alt="Job System">
  <img src="https://img.shields.io/badge/Android-3DDC84?style=for-the-badge&logo=android&logoColor=white" alt="Android">
  <img src="https://img.shields.io/badge/iOS-000000?style=for-the-badge&logo=apple&logoColor=white" alt="iOS">
</p>

A falling sand alchemy puzzle for Android and iOS, built as a mobile performance engineering study.

The game is the vehicle. The point is running a cellular automaton of roughly 150,000 cells at 60 fps on a mid range Android phone, and being able to prove it.

| | |
|---|---|
| **Storage** | `NativeArray<uint>`, 4 bytes per cell, bit packed. No per cell objects. |
| **Sleeping** | 32×32 chunks with dirty rects. Settled chunks are skipped entirely. |
| **Threading** | Checkerboard phasing, four non adjacent groups, `IJobParallelFor`. No locks, no atomics. |
| **Determinism** | Position independent hash of `(tick, cellIndex)`. No shared RNG, so results never depend on thread scheduling. |
| **Allocation** | Every buffer allocated once with `Allocator.Persistent`. Target is 0 B of GC allocation per frame. |
| **Rendering** | The whole grid is one texture on one quad. One draw call for the play area. |

The build ships a diagnostic overlay with runtime A/B switches for chunking, jobs and Burst, so the cost of each optimization can be toggled on a real device rather than argued about. A naive reference implementation stays in the repository permanently, and an equivalence test asserts the optimized simulation produces a bit identical grid. A performance change that cannot pass that test is a bug, not an optimization.

<img src="https://raw.githubusercontent.com/Nomracer/Nomracer/main/.assets/rule.svg" width="100%" height="3" alt="">

## Stack

<p>
  <img src="https://img.shields.io/badge/Unity-000000?style=for-the-badge&logo=unity&logoColor=white" alt="Unity">
  <img src="https://img.shields.io/badge/C%23-512BD4?style=for-the-badge&logo=csharp&logoColor=white" alt="C#">
  <img src="https://img.shields.io/badge/Java-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white" alt="Java">
  <img src="https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black" alt="JavaScript">
  <img src="https://img.shields.io/badge/Android-3DDC84?style=for-the-badge&logo=android&logoColor=white" alt="Android">
  <img src="https://img.shields.io/badge/iOS-000000?style=for-the-badge&logo=apple&logoColor=white" alt="iOS">
</p>

**Engine** &nbsp; Unity 6 · URP · 2D Renderer<br>
**Performance** &nbsp; Burst · Job System · Native Collections · Unity Profiler · Memory Profiler · Profile Analyzer<br>
**Platforms** &nbsp; Android (IL2CPP, ARM64, Vulkan and GLES3) · iOS (Metal)
