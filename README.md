# annealed_langevin_dynamics-stepsequencer-qt

A step sequencer for the denoising trajectory. Program the generation like a pattern; chain patterns into songs.

## The name

Ancestral (stochastic) sampling in diffusion models literally *is* annealed Langevin dynamics — Paul Langevin, 1908, Brownian motion. The name is the most technically correct description of what the instrument plays, and it doubles as camouflage: nobody skimming GitHub reads "AI art" in it. Descriptive to those who know, boring to those who don't.

## The idea

A diffusion generation is a trajectory: N steps from pure noise to image. Every existing UI treats the trajectory as something that happens *to* you. This treats it as something you *compose*.

Each step of the sequence holds:

- **prompt** — prompt scheduling: different prompts at different step ranges (early steps govern composition, late steps govern texture)
- **CFG scale** — guidance scheduling: hot early for composition, eased off late so textures breathe
- **sampler parameters** — switch solvers mid-flight; per-step stochasticity / churn (the whammy bar between aesthetic valleys)
- **schedule curvature** — bend the noise schedule: linger in mid-noise where texture and material get decided

64 steps. Program the whole generation like a drum pattern. Chain patterns into songs.

## Why a sequencer, not a keyboard

Composition beats performance. You don't play it live — you tell it what notes you want. The 808 proved this in 1981: the step sequencer democratized rhythm by making it programmable. Same move, new medium.

## Mapping (modular synth terms)

| Trajectory concept | Synth equivalent |
|---|---|
| scheduler | sequencer — order and timing of steps |
| sampler | oscillator/filter topology — character of each step |
| CFG | filter cutoff — how hard the prompt shapes the output |
| noise | raw waveform |
| stochasticity (churn) | whammy bar between aesthetic valleys |

## The `-qt` suffix

Native Qt frontend, per the goose-qt convention: the native shell is the correct tool for a workstation. No browser jank.

## Status

Spec stage. Bare bones. One instrument in the righteous dub arc.
