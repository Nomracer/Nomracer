<h1 align="center">Gürkan Şimşek</h1>

<p align="center">
  Unity developer. I care about what a game costs per frame on hardware people actually own.
</p>

<p align="center">
  <a href="https://nomracer.itch.io/"><img src="https://img.shields.io/badge/itch.io-play%20my%20games-FA5C5C?style=for-the-badge&logo=itchdotio&logoColor=white" alt="itch.io"></a>
  <a href="https://github.com/Nomracer/Crucible"><img src="https://img.shields.io/badge/Crucible-read%20the%20code-2E2E2E?style=for-the-badge&logo=github&logoColor=white" alt="Crucible"></a>
</p>

<br>

## Dead Frame

<a href="https://nomracer.itch.io/dead-frame">
  <img src="https://img.itch.zone/aW1nLzI4MTkyMjE1LnBuZw==/original/ooc3EM.png" width="420" align="right" alt="Dead Frame cover">
</a>

Psychological horror. You are a trainee in a Veyks encounter simulation. Survive four nights and get educated, because your life depends on it.

Roughly half an hour per run. Subtitles and remappable controls. Windows.

Two months of development, shipped and playable right now.

<a href="https://nomracer.itch.io/dead-frame"><img src="https://img.shields.io/badge/▶%20PLAY%20DEAD%20FRAME-on%20itch.io-FA5C5C?style=for-the-badge" alt="Play Dead Frame"></a>

<br clear="all">

<br>

## Crucible

**[github.com/Nomracer/Crucible](https://github.com/Nomracer/Crucible)**

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

<br>

## Stack

**Engine** &nbsp; Unity 6 · URP · 2D Renderer<br>
**Performance** &nbsp; Burst · Job System · Native Collections · Unity Profiler · Memory Profiler · Profile Analyzer<br>
**Languages** &nbsp; C# · Java · JavaScript<br>
**Platforms** &nbsp; Android (IL2CPP, ARM64, Vulkan and GLES3) · iOS (Metal)
