# Changelog

## v0.1.0 — Verified Starter Kit

### Added

- Lean 4 starter specification for the Alignment 5/5 verification model
- fail-safe and causal composition proofs in the formal model
- reproducible benchmark harness and artifact generation
- proof-boundary documentation separating proved claims from axioms
- release checklist and publication guidance

### Verified scope

- Build passes with `lake build`
- Benchmark artifacts are generated in the `results/` directory
- The starter package is not a full AI safety certification

### Not yet claimed

- complete regulator-grade proof coverage
- proof of the PAC latent bound beyond the starter axiom
- deployment-grade safety certification for real systems
