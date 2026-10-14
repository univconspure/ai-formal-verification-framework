# Release v0.1.0

## Summary

This release packages the Alignment 5/5 Verified Starter Kit as a reproducible Lean 4 + benchmark project with explicit proof boundaries.

## Verified evidence

- `lake build` completed successfully
- `python benchmarks/run_benchmarks.py --n 50 --out results` generated benchmark artifacts
- output files were written to `results/benchmark_results.json`, `results/benchmark_results.csv`, and `results/SHA256SUMS.txt`

## Included artifacts

- `README.md`
- `Alignment55.lean`
- `Alignment55/Basic.lean`
- `proofs/Proofs_Outline.md`
- `benchmarks/run_benchmarks.py`
- `results/benchmark_results.json`
- `results/benchmark_results.csv`
- `results/SHA256SUMS.txt`
- `RELEASE_CHECKLIST.md`

## Public claim boundary

This release supports the statement that the starter package is buildable and reproducible. It does not claim full end-to-end AI safety certification or a completed PAC latent-bound proof.

## Release tag

`v0.1.0`
