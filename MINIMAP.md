# MINIMAP — annealed_langevin_dynamics-stepsequencer-qt (hand this + the relevant source files to any model)

## What this is
A step sequencer for the denoising trajectory of a diffusion model —
program the generation like a pattern; chain patterns into songs. A Qt
music tool, not a game. One instrument in the righteous dub arc.

The name is the most technically correct description of what the
instrument plays, and doubles as camouflage: ancestral (stochastic)
sampling in diffusion models literally *is* annealed Langevin
dynamics (Paul Langevin, 1908, Brownian motion). Descriptive to those
who know, boring to those who don't — nobody skimming GitHub reads
"AI art" in it.

## Current state (as found on main) — SPEC STAGE, NO CODE
- **The repo contains exactly one file: `README.md`.** No src/, no
  build files, no run.bat, no GOALS.md, no docs/. There is nothing to
  build or run. The README is the whole project so far: "Spec stage.
  Bare bones."
- No build number exists. Do not claim one.
- The first real work is Build 1 (the skeleton app), following the
  house Qt pattern of the sibling projects.

## The idea (from the README — the spec, not implemented code)
A diffusion generation is a trajectory: N steps from pure noise to
image. Every existing UI treats the trajectory as something that
happens *to* you. This treats it as something you *compose*.

Each step of the sequence holds:
- **prompt** — prompt scheduling: different prompts at different step
  ranges (early steps govern composition, late steps govern texture)
- **CFG scale** — guidance scheduling: hot early for composition,
  eased off late so textures breathe
- **sampler parameters** — switch solvers mid-flight; per-step
  stochasticity / churn (the whammy bar between aesthetic valleys)
- **schedule curvature** — bend the noise schedule: linger in
  mid-noise where texture and material get decided

64 steps. Program the whole generation like a drum pattern. Chain
patterns into songs.

Why a sequencer, not a keyboard: composition beats performance. You
don't play it live — you tell it what notes you want. The 808 proved
this in 1981: the step sequencer democratized rhythm by making it
programmable. Same move, new medium.

## Mapping (modular synth terms, from the README)
| Trajectory concept | Synth equivalent |
|---|---|
| scheduler | sequencer — order and timing of steps |
| sampler | oscillator/filter topology — character of each step |
| CFG | filter cutoff — how hard the prompt shapes the output |
| noise | raw waveform |
| stochasticity (churn) | whammy bar between aesthetic valleys |

## Layout
```
README.md                The whole project: name, idea, per-step
                         parameters, synth mapping, -qt rationale,
                         status (spec stage)
```

## The `-qt` suffix
Native Qt frontend, per the goose-qt convention: the native shell is
the correct tool for a workstation. No browser jank. (When Build 1
lands, the intended stack is Qt — the sibling Qt projects use C++17 /
Qt6 / CMake + MinGW on Penny's PC; verify against the actual first
build rather than assuming.)

## Build and run — NOT YET POSSIBLE (no code)
When Build 1 lands, the house ABI applies: `git pull`, then
`.\run.bat` (run.bat always builds; see the sibling projects'
run.bats for the pattern).

## Gotchas
- **No code, no build, no version** — everything in this repo is one
  README. The next agent's job is Build 1, not a minimap update.
- The name is camouflage by design (see above) — do not "clarify" it
  into something that reads as AI art on a skim.
- The 64-step scope and the four per-step parameters (prompt, CFG,
  sampler params, schedule curvature) are the spec's load-bearing
  numbers; the first build should implement them, not a reduced set.
