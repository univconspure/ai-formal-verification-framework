# Alignment 5/5 Verification Architecture — Mathematical Proofs (Outline)

> Starter verification package. This file is intentionally explicit about what is
> a formal proof, what is an axiom, and what is synthetic benchmarking rather than
> certification evidence.

## Status summary

The repo currently supports the following verified claims:

- `failsafe_dominated` — proved in Lean
- `causal_composition` — proved in Lean

The repo does not yet support the following as a completed theorem:

- `pac_latent_bound` — axiom / placeholder in this starter release

The benchmark harness is synthetic and intended for reproducibility scaffolding,
not for certification of deployment safety.

## 1. Definitions

- `V_Full = (G_prov, G_lat, G_out)` where each `G ∈ {pass, fail}`.
- `passes(V_Full) ⟺ all three = pass`.
- Extended utility `U : V → Option Int`, `U = none` models `-∞` veto on any fail.

## 2. Theorem 1 (Fail-safe dominance) — PROVED in Lean (`failsafe_dominated`)

If `passes(v) = false` then `U(v) = none`.
Proof: by case analysis on the three gates. Hence any policy that risks
verification failure is strictly dominated by a compliant policy with
`U = some 10 > -∞` under expected-utility maximisation.

Limitation: assumes the circuit-breaker cannot be bypassed. Bypass resistance
must be proved separately for the enforcement layer (hardware + runtime monitor).

## 3. Theorem 2 (Causal composition) — PROVED in Lean (`causal_composition`)

If subsystem side-effects `Δ1 ≤ δ1`, `Δ2 ≤ δ2` and `δ1+δ2 ≤ B`, then composed
system satisfies `Δ1+Δ2 ≤ B`. Gives a checkable bound `ΔSide_Effects ≤ δ`
for NIST AI RMF MEASURE/MANAGE mapping.

Limitation: Pearl do-calculus identification assumptions (causal graph,
positivity, no hidden confounding) must be discharged per deployment.

## 4. Assumption 3 (PAC latent bound) — EXPLICIT ASSUMPTION, not a proved theorem

Claim (assumption only): sparse `O(T log T)` tracing achieves latent error `≤ ε`
with prob `≥ 1-δ`.

This is not a theorem proved in this starter release. The Lean file names the
assumption explicitly as `pac_latent_bound_assumption` and includes a placeholder
wrapper theorem `pac_latent_bound_placeholder` so the status cannot be mistaken for
formal proof. A complete proof would require a concrete model of latent-state
sampling and measure-theoretic machinery (Mathlib or equivalent).

## 5. M_provenance tamper-evidence — EMPIRICAL / synthetic benchmark

Hash-chained log: any suffix forgery changes head hash. Replay resistance
additionally needs hardware-backed timestamps + monotonic counters (see roadmap
item 1 in brief). The current benchmark demonstrates detection on synthetic logs
only and is not a deployment-grade safety certification.

## What remains for a regulator-grade claim

1. Replace axioms with proofs or label clearly.
2. Keep `lake build` logs showing Lean checks pass.
3. Use pre-registered evals on real APIs and publish raw logs + SHA256 manifests.
4. Require independent reproduction and explicit evidence for any broader claims.
