# v0.1.0 — Verified Starter Kit

This release packages the Alignment 5/5 Verified Starter Kit as a reproducible Lean 4 + benchmark project with explicit proof boundaries.

## What is included

- Lean 4 starter specification for the Alignment 5/5 verification model
- proof-boundary documentation distinguishing formal proofs from axioms
- reproducible benchmark harness and generated artifacts
- release and publication guidance for future public release workflows

## Verified evidence

The repository was validated with fresh evidence:

- `lake build` → `Build completed successfully.`
- `python benchmarks/run_benchmarks.py --n 50 --out results`
- benchmark artifacts were generated in `results/`

Artifacts included in this release:

- `README.md`
- `Alignment55.lean`
- `Alignment55/Basic.lean`
- `proofs/Proofs_Outline.md`
- `benchmarks/run_benchmarks.py`
- `results/benchmark_results.json`
- `results/benchmark_results.csv`
- `results/SHA256SUMS.txt`
- `RELEASE_CHECKLIST.md`

## Current scope and claim boundary

This release supports the claim that the starter package is buildable and reproducible.

It does not claim:

- full regulator-grade AI safety certification
- completed proof coverage for all high-level architecture claims
- formal proof of the PAC latent-bound theorem beyond the starter assumption/model boundary

## Verified claims in scope

The starter repo includes Lean-verified results for:

- `failsafe_dominated`
- `causal_composition`

The remaining PAC latent-bound statement is intentionally described as a model/assumption boundary in the proof outline and should not be cited as a formally proven theorem.

## Release metadata

- Version: `0.1.0`
- Lean build status: passing
- Release artifacts: included in the tagged GitHub release
