# Alignment 5/5 Verification Architecture — Verified Starter Kit

This repository is a working starter proof-and-benchmark package for the Alignment 5/5 Verification Architecture. It is designed to make an auditable, reproducible claim about the formal specification, proof boundary, and benchmarking workflow without overstating what has been completed.

## Verified status

This repository has been validated at the starter-project level with fresh evidence:

```bash
cd "c:/.../alignment55-verfication-v0.10"
lake build
python benchmarks/run_benchmarks.py --n 50 --out results
```

Observed result on 2026-10-14:

- `lake build` → `Build completed successfully.`
- benchmark runner → wrote `results/benchmark_results.json`, `results/benchmark_results.csv`, and `results/SHA256SUMS.txt`

## Contents

- `Alignment55/Basic.lean` — Lean 4 formal spec for `GateResult`, `VFull`, fail-safe utility, and causal composition
- `Alignment55.lean` — module entry point
- `proofs/Proofs_Outline.md` — explicit proof boundary: what is proved vs assumed vs empirical
- `benchmarks/run_benchmarks.py` — reproducible synthetic benchmark harness
- `results/` — generated JSON/CSV/hash artifacts
- This README — verification and publication checklist

## What is currently proved

The Lean starter includes verified results for:

- `failsafe_dominated`
- `causal_composition`

These are formalized in `Alignment55/Basic.lean` and build successfully.

## What is not yet proved

The PAC latent-bound claim remains explicitly scoped as a model/assumption boundary in the starter spec:

- the latent bound is not a completed theorem in this repository
- the benchmark is synthetic and intended as a scaffold, not a certification of real deployment behavior

This is not a regulator-grade safety guarantee. It is a reproducible starter verification package with transparent scope boundaries.

## Publication guidance

Use this wording when the project is not yet published:

> Prototype Lean 4 specifications, proof outlines, and benchmarking harnesses for the Alignment 5/5 Verification Architecture are prepared for release. The formal verification scope is partial and explicitly bounded: the starter repo includes buildable Lean proofs for the fail-safe and causal composition claims, while the PAC latent bound remains an axiom and independent reproduction is pending.

Use this wording only after public release and artifact publication:

> Starter Lean 4 specifications (commit `<SHA>`, `lake build` passing), proof outlines distinguishing proved theorems from axioms, and benchmarking artifacts with SHA256 manifests are publicly accessible at [GitHub URL] (release `<tag>`) and associated publication record `<URL>`. Independent reproduction is pending or confirmed by `<who, date>`.

## Reproducibility checklist

1. Install Lean 4 toolchain and run `lake build`
2. Run the benchmark harness: `python benchmarks/run_benchmarks.py --n 50 --out results`
3. Preserve generated artifacts in `results/`
4. Publish the repo, commit SHA, and release URL before making stronger public claims

## Release metadata

- Version: `0.1.0`
- Release file: `release-v0.1.0.md`
- Changelog: `CHANGELOG.md`
- Public status: verified starter package with transparent proof boundaries

## GitHub release workflow

Use this exact sequence before publishing a release:

```bash
cd "c:/.../alignment55-verfication-v0.10"
lake build
python benchmarks/run_benchmarks.py --n 200 --out results
sha256sum results/* > results/SHA256SUMS.txt
git status --short
git add README.md Alignment55 Alignment55.lean proofs benchmarks results VERSION CHANGELOG.md release-v0.1.0.md
git commit -m "Release v0.1.0: verified starter kit"
git tag v0.1.0
git push origin main --tags
```

Record the following values for any public claim:

- repository URL
- commit SHA: `git rev-parse HEAD`
- release tag: `v0.1.0`
- artifact hash manifest: `results/SHA256SUMS.txt`
- Lean version used by the build

## Why this matters

The repository is now aligned with the evidence: it is a verified starter package with clear proof boundaries, not a claim of complete end-to-end AI safety certification.
