# Release Checklist

This checklist is intended for a truthful public release of the Alignment 5/5 Verified Starter Kit.

## 1. Preflight validation

Run the project verification commands and keep the output logs:

cd "c:/Users/coolh/OneDrive/Documents/GitHub/alignment55-verfication-v0.10"
```bash
lake build
python benchmarks/run_benchmarks.py --n 200 --out results
sha256sum results/* > results/SHA256SUMS.txt
```

Keep the terminal output showing:

- `Build completed successfully.`
- benchmark files created in `results/`
- SHA256 manifest generated

## 2. Record evidence

Capture the following before publishing:

```bash
git rev-parse HEAD
lean --version
```

Record the result in the release notes or GitHub release body.

## 3. Git commit and tag

```bash
git status --short
git add README.md Alignment55 Alignment55.lean proofs benchmarks results
git commit -m "Release v0.1.0: verified starter kit"
git tag v0.1.0
git push origin main --tags
```

## 4. Publish on GitHub

Create a release named `v0.1.0` and attach these artifacts:

- `README.md`
- `Alignment55.lean`
- `Alignment55/Basic.lean`
- `proofs/Proofs_Outline.md`
- `results/benchmark_results.json`
- `results/benchmark_results.csv`
- `results/SHA256SUMS.txt`

Include in the release notes:

- repository URL
- commit SHA
- tag name
- Lean version used
- description of what is proved vs what is still an axiom

## 5. Public claim boundaries

The public claim should stay within the validated scope:

- Verified: starter Lean proofs for fail-safe dominance and causal composition
- Not yet claimed: full regulator-grade AI safety certification
- Not yet claimed: proof of PAC latent-bound theorem beyond the starter axiom

## 6. Suggested wording

> Starter Lean 4 specifications (commit `<SHA>`, `lake build` passing on Lean `<version>`), proof outlines distinguishing proved theorems from axioms, and benchmarking artifacts with SHA256 manifests are publicly accessible at [GitHub URL] (release v0.1.0). Independent reproduction remains pending or confirmed by `<who, date>`.
